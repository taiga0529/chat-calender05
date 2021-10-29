# chat-calender05
# アプリケーション概要

# url

# テスト用アカウント

# 利用方法
お仕事のスケジュールの大まかな進め方、日程をカレンダーに記載し、そのままアプリを変えることなくチャットができるアプリケーションです。
# 目指した課題解決
お仕事の連絡、スケジュール管理がまとめてできたら便利でスケジュールの確認ミスも減るのではないかと考えました。
また、チームで開発をする際や、職業によってはチームで連絡を取り合いながら作業するお仕事もあると思うのでスケジュール通り進んでいるかカレンダーを見ながら把握したりそのままチャットできれば便利で楽だなと思ったからです。
# 要件
# 実装予定の機能
ユーザー管理機能、チャット機能、カレンダー機能、グループチャット機能、画像の送信機能
# README
# テーブル設計

## users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| name               | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |

### Association

- has_many :room_users
- has_many :rooms, through: :room_users
- has_many :messages

## rooms テーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| name   | string | null: false |

### Association

- has_many :room_users
- has_many :users, through: :room_users
- has_many :messages

## room_users テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user

## messages テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user