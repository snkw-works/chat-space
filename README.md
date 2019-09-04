# DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|id|integer|null: false, foreign_key: true|
|name|string|null: false, index: true|
|email|string|null: false, unique: true|
|password|string|null: false|

### Association
- has_many :groups, through: :group_users
- has_many :group_users
- has_many :messages

## group_usersテーブル
|Column|Type|Options|
|------|----|-------|
|group_id|references|null: false, foreign_key: true|
|user_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|id|integer|null: false, foreign_key: true|
|name|string|null: false|

### Association
- has_many :users, through: :group_users
- has_many :messages
- has_many :group_users

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|id|integer|null: false, foreign_key: true|
|text|text||
|image|string||
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user