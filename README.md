# Tugas 2 Framework Laravel - Book & Author

Proyek aplikasi web sederhana berbasis Framework Laravel yang mengimplementasikan sistem basis data relasional dengan studi kasus **Book dan Author**. Proyek ini mencakup pembuatan Laravel Migration, Laravel Seeder, Eloquent Model, Controller, Blade View berbasis Bootstrap 5, serta Routing.

**Nama Mahasiswa:** Zulfaqih Ashar Hasan  
**Kampus:** Universitas Trisakti  
**Mata Kuliah / Program:** Studi Independen - Pemrograman PHP / Framework Laravel  

---

## 🗄️ Struktur Tabel & Database

### 1. Tabel `authors`
| Kolom | Tipe Data | Keterangan |
| :--- | :--- | :--- |
| `id` | BigIncrements (Primary Key) | ID unik penulis |
| `name` | String | Nama lengkap penulis |
| `country` | String | Asal negara (default: 'Indonesia') |
| `bio` | Text (nullable) | Profil dan biografi singkat |
| `created_at` & `updated_at` | Timestamps | Waktu pembuatan & pembaruan data |

### 2. Tabel `books`
| Kolom | Tipe Data | Keterangan |
| :--- | :--- | :--- |
| `id` | BigIncrements (Primary Key) | ID unik buku |
| `author_id` | ForeignId (Unsigned BigInteger) | Foreign Key merujuk ke `authors.id` (`onDelete('cascade')`) |
| `title` | String | Judul buku |
| `year` | Integer | Tahun publikasi/terbit |
| `description` | Text (nullable) | Sinopsis / ringkasan buku |
| `created_at` & `updated_at` | Timestamps | Waktu pembuatan & pembaruan data |

---

## 📂 Berkas Tugas

1. **Migration:**
   - `database/migrations/2026_01_01_000001_create_authors_table.php`
   - `database/migrations/2026_01_01_000002_create_books_table.php`

2. **Model:**
   - `app/Models/Author.php` (relasi `hasMany(Book::class)`)
   - `app/Models/Book.php` (relasi `belongsTo(Author::class)`)

3. **Seeder:**
   - `database/seeders/AuthorSeeder.php` (5 data penulis Indonesia)
   - `database/seeders/BookSeeder.php` (5 data buku terkait penulis)
   - `database/seeders/DatabaseSeeder.php` (pemanggilan seeder secara berurutan)

4. **Controller:**
   - `app/Http/Controllers/AuthorController.php`
   - `app/Http/Controllers/BookController.php`

5. **View & Layout:**
   - `resources/views/layouts/app.blade.php` (Layout utama Bootstrap 5)
   - `resources/views/home.blade.php` (Halaman Beranda)
   - `resources/views/authors/index.blade.php` (Tabel data Author)
   - `resources/views/books/index.blade.php` (Tabel data Book)

6. **Routing:**
   - `routes/web.php` (Route `/`, `/books`, `/authors`)

---

## 🚀 Panduan Menjalankan Proyek

### 1. Menjalankan Migration dan Seeder
```bash
php artisan migrate:fresh --seed
```

### 2. Menjalankan Server Laravel
```bash
php artisan serve
```

Server akan aktif pada `http://127.0.0.1:8000`.

---

## 🌐 Daftar URL Halaman

- **Beranda:** `http://127.0.0.1:8000/`
- **Halaman Book:** `http://127.0.0.1:8000/books`
- **Halaman Author:** `http://127.0.0.1:8000/authors`
