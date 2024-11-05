# Lavarel note

## Cấu trúc dự án

__Lưu ý__: Có 2 folder dành cho 2 trang admin và user riêng

```
project-root/
│
├── app/                # Thư mục chứa các lớp ứng dụng chính
│   ├── Console/        # Các lệnh Artisan tùy chỉnh
│   ├── Exceptions/     # Các lớp xử lý ngoại lệ
│   ├── Http/           # Controllers, middleware, requests, và các lớp liên quan đến HTTP
│   │   ├── Controllers/
│   │   ├── Middleware/
│   │   └── Requests/
│   ├── Models/         # Các model Eloquent
│   ├── Providers/      # Các service provider
│   └── ...             # Các thư mục khác
│
├── bootstrap/          # Các tập tin khởi tạo của ứng dụng
│   ├── app.php         # Tập tin bootstrap của ứng dụng
│   └── cache/          # Thư mục lưu cache
│
├── config/             # Các tệp cấu hình của ứng dụng
│   ├── app.php         # Cấu hình chung của ứng dụng
│   ├── database.php    # Cấu hình cơ sở dữ liệu
│   ├── mail.php        # Cấu hình email
│   └── ...             # Các tệp cấu hình khác
│
├── database/           # Các tệp liên quan đến cơ sở dữ liệu
│   ├── factories/      # Các factory dùng để tạo mẫu dữ liệu giả
│   ├── migrations/     # Các migration của cơ sở dữ liệu
│   └── seeders/        # Các seeder (dữ liệu mẫu) cho cơ sở dữ liệu
│
├── lang/               # Các tệp ngôn ngữ của ứng dụng
│   └── en/             # Ví dụ: Tệp ngôn ngữ tiếng Anh
│       └── messages.php
│
├── public/             # Thư mục chứa các tệp công khai, bao gồm index.php và tài nguyên tĩnh
│   ├── css/            # Tệp CSS
│   ├── js/             # Tệp JavaScript
│   ├── images/         # Hình ảnh
│   └── index.php       # Điểm bắt đầu của ứng dụng web
│
├── resources/          # Tệp tài nguyên chưa biên dịch (views, lang, assets)
│   ├── views/          # Các file blade templates (view)
│   ├── lang/           # Tệp ngôn ngữ cho views
│   └── sass/           # Tệp SASS (nếu có)
│
├── routes/             # Các file định nghĩa các routes
│   ├── web.php         # Routes cho giao diện web
│   ├── api.php         # Routes cho API
│   └── console.php     # Các route cho Artisan commands
│
├── storage/            # Thư mục lưu trữ dữ liệu tạm thời (logs, cache, sessions)
│   ├── app/            # Các file tải lên và file của ứng dụng
│   ├── framework/      # Dữ liệu của framework (logs, cache, sessions)
│   └── logs/           # Tệp logs của ứng dụng
│
├── tests/              # Các tệp kiểm thử ứng dụng
│   ├── Feature/        # Các test kiểm tra tính năng
│   ├── Unit/           # Các test kiểm tra đơn vị
│   └── TestCase.php    # Lớp cơ sở cho tất cả các test
│
├── .env                # Tệp cấu hình môi trường (mặc định không được lưu trong hệ thống version control)
├── .gitignore          # Các file và thư mục sẽ bị loại trừ khỏi Git
├── artisan             # Tệp command line của Laravel (CLI)
├── composer.json       # Các package và phụ thuộc của dự án
├── package.json        # Các phụ thuộc phía frontend (nếu có)
├── phpunit.xml         # Cấu hình PHPUnit cho các test
└── README.md           # Tệp hướng dẫn và mô tả về dự án
```
## Clone project về máy

1.	Run git clone 'link projer github'
2.	Run composer install
3.	Run cp .env.example .env or copy .env.example .env
4.	Run php artisan key:generate
5.	Run php artisan migrate
6.	Run php artisan db:seed
7.	Run php artisan serve


## Thêm nhanh user

```php
php artisan tinker
$user = new App\Models\User;
$user->name = 'Tên mới';
$user->email = 'email@domain.com';
$user->password = bcrypt('passwor#d');
$user->save();
```

## Cập nhật user 


```php
php artisan tinker
$user = App\Models\User::find(1); // Tìm người dùng có ID là 1
$user->name = 'Tên đã cập nhật';
$user->save();
```

## Phân quyền người dùng

```php
$user = User::find(1);
$user->assignRole('admin');
```

## In tất cả người dùng 

```php
$users = App\Models\User::all();
$users->toArray();  
```