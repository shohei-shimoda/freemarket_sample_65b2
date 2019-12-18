# README

# メルカリ
## usersテーブル

|Column|Type|Options|
|------|----|-------|
|nickname|text|index: true, null: false, unique: true|
|e-mail|integer|null: false, unique: true|
|password|integer|null: false|
|first_name|string|null: false|
|last_name|string|null: false|
|first_name_kana|string|null: false|
|last_name_kana|string|null: false|
|birthday_year|integer|null: false|
|birthday_month|integer|null: false|
|birthday_day|integer|null: false|
|phone_num|integer|null: false|
|authentication_num|integer|null: false|
|user_img|text||
|introduction|text||

### Association
- has_one :addresses
- has_one :cards
- has_one :buyers
- has_many :items
- has_many :comments

## addressesテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|first_name|string|null: false|
|last_name|string|null: false|
|first_name_kana|string|null: false|
|last_name_kana|string|null: false|
|postcode|integer|null: false|
|prefecture|string|null: false|
|city|string|null: false|
|house_num|integer|null: false|
|buiding_name|string||
|phone_num|integer|null: false|

### Association
- belongs_to :users
- has_many :items

## cardsテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|card_num|integer|null: false|
|limit_month|integer|null: false|
|limit_year|integer|null: false|
|security_code|integer|null: false|

### Association
- belongs_to :users
- has_many :items
- has_many :buyers

## itemsテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|item_image|string|null: false|
|name|text|null: false|
|description|text|null: false|
|condition|integer|null: false|
|delivery_charge|integer|null: false|
|delivery_area|integer|null: false|
|delivery_days|integer|null: false|
|price|integer|null: false|
|saller_id|integer|null: false|
|status|integer|null: false|

### Association
- belongs_to :users
- belongs_to :items
- belongs_to :buyers
- has_many :comments

## buyersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|item_id|references|null: false, foreign_key: true|
|status|integer|null: false|

### Association
- belongs_to :users
- belongs_to :cards
- has_many :comments
- has_many :items

## commentsテーブル

|Column|Type|Options|
|------|----|-------|
|content|text|null: false|
|user_id|references|null: false, foreign_key: true|
|items_id|references|null: false, foreign_key: true|

### Association
- belongs_to :users
- has_many :items
- has_many :buyers