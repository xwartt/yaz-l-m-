# 🛒 Basit E-Ticaret Uygulaması

# Ürün listesi
products = {
    1: {"name": "Laptop", "price": 15000},
    2: {"name": "Telefon", "price": 8000},
    3: {"name": "Kulaklık", "price": 500}
}

# Sepet
cart = []

# Ürünleri listele
def list_products():
    print("\n📦 Mevcut Ürünler:")
    for pid, info in products.items():
        print(f"{pid}. {info['name']} - {info['price']} TL")

# Sepete ürün ekle
def add_to_cart(product_id):
    if product_id in products:
        cart.append(products[product_id])
        print(f"✅ {products[product_id]['name']} sepete eklendi.")
    else:
        print("❌ Geçersiz ürün ID.")

# Sepeti göster
def show_cart():
    print("\n🛍️ Sepetiniz:")
    if not cart:
        print("Sepetiniz boş.")
        return
    total = 0
    for item in cart:
        print(f"- {item['name']} - {item['price']} TL")
        total += item['price']
    print(f"💰 Toplam: {total} TL")

# Ödeme simülasyonu
def checkout():
    if not cart:
        print("Sepetiniz boş, ödeme yapılamaz.")
        return
    show_cart()
    confirm = input("Ödemeyi onaylıyor musunuz? (E/H): ")
    if confirm.lower() == 'e':
        print("🎉 Ödeme başarılı! Siparişiniz alındı.")
        cart.clear()
    else:
        print("🚫 Ödeme iptal edildi.")

# Ana menü
def main():
    while True:
        print("\n📋 Menü:\n1. Ürünleri Listele\n2. Sepete Ekle\n3. Sepeti Göster\n4. Ödeme Yap\n5. Çıkış")
        choice = input("Seçiminiz: ")
        if choice == '1':
            list_products()
        elif choice == '2':
            try:
                pid = int(input("Ürün ID girin: "))
                add_to_cart(pid)
            except ValueError:
                print("Lütfen geçerli bir sayı girin.")
        elif choice == '3':
            show_cart()
        elif choice == '4':
            checkout()
        elif choice == '5':
            print("👋 Çıkış yapılıyor...")
            break
        else:
            print("⚠️ Geçersiz seçim.")

# Uygulamayı başlat
if __name__ == "__main__":
    main()
