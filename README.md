# テーブル設計

## users テーブル

| Column   | Type   | Options     | 
| -------- | ------ | ----------- | 
| name     | string | null: false | 
| email    | string | null: false | 
| password | string | null: false | 

### Association

- has_many :room_users
- has_many :rooms, through: room_users
- has_many :messages

## rooms テーブル

| Colunm | Type   | Options     | 
| ------ | ------ | ----------- | 
| name   | string | null: false | 

### Assosiation

- has_many :room_users
- has_many :users, through: room_users
- has_many :messages

## room_users テーブル

| Colunm | Type       | Options                        | 
| ------ | ---------- | ------------------------------ | 
| user   | references | null: false, foreign_key: true | 
| room   | references | null: false, foreign_key: true | 

### Assosiation

- belongs_to :room
- belongs_to :user

## messages テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |

### Assosiation

- belongs_to :room
- belongs_to :user