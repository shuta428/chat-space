# ChatSpace DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|Name|string|null: false|
|Email|string|null: false|
|Password|string|null: false|
### Association
- has_many :group
- has_many :message
- has_many :groups_users

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|string|null: false|
|group_id|integer|null: false, foreign_key:true|
|user_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|Name|string|null: false|
|user_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :users
- has_many :messages
- has_many :groups_users

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
