# DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique:true|
|mail|string|null: false, unique:true|
|password|string|null: false|

### Association
- has_many :groups, through :members
- has_many :messages
- has_many :members


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique:true|

### Association
- has_many :users, through :members
- has_many :messages
- has_many :members


## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
|body|text|null: false|
|image|string||

### Association
- belongs_to :group
- belongs_to :user


## membersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user