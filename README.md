# WeHelp-week5-MySQL

## 要求二
![截圖 2022-10-17 下午2 37 26](https://user-images.githubusercontent.com/75289113/196105807-60578e5d-181b-407c-8e88-377b69fbef53.png)


## 要求三
### 使⽤ INSERT 指令新增⼀筆資料到 member 資料表中，這筆資料的 username 和 password 欄位必須是 test。接著繼續新增⾄少 4 筆隨意的資料。
``` sql
Insert into member (name, username, password, follower_count) values('test', 'test', 'test', 10);
```
-   ![截圖 2022-10-17 下午2 50 13](https://user-images.githubusercontent.com/75289113/196108019-d6af6266-5e98-4ce4-ba09-0b0b2a9e9d98.png)
``` sql
Insert into member (name, username, password, follower_count) values
('amy', 'amy', 'amy', 20),
('ted', 'ted', 'ted', 30),
('nick', 'nick', 'nick', 40),
('rick', 'rick', 'rick', 50);
```
- ![截圖 2022-10-17 下午2 57 17](https://user-images.githubusercontent.com/75289113/196109368-35f61f5c-4f83-4624-9856-cfd6ab984f4c.png)

### 使⽤ SELECT 指令取得所有在 member 資料表中的會員資料。
```sql
select * from member;
```
- ![截圖 2022-10-17 下午3 01 41](https://user-images.githubusercontent.com/75289113/196110103-f701cd3c-9eb7-495f-873b-930eb84fd590.png)

### 使⽤ SELECT 指令取得所有在 member 資料表中的會員資料，並按照 time 欄位，由近到遠排序。
```sql
select * from member order by time desc;
```
- ![截圖 2022-10-17 下午3 04 14](https://user-images.githubusercontent.com/75289113/196110536-6d78f4fe-cc0e-42f3-8960-7123c04bc785.png)

### 使⽤ SELECT 指令取得 member 資料表中第 2 ~ 4 共三筆資料，並按照 time 欄位，由近到遠排序。
```sql
select * from member order by time desc limit 1, 3;
```
- ![截圖 2022-10-17 下午3 12 03](https://user-images.githubusercontent.com/75289113/196111839-96518bd8-4dee-4cff-b0c4-48dd56491369.png)

### 使⽤ SELECT 指令取得欄位 username 是 test 的會員資料。
```sql
select * from member where username = 'test';
```
- ![截圖 2022-10-17 下午3 14 26](https://user-images.githubusercontent.com/75289113/196112246-1aee01e1-7ee1-487c-a8ba-080227000a36.png)

### 使⽤ SELECT 指令取得欄位 username 是 test、且欄位 password 也是 test 的資料。
```sql
select * from member where username = 'test' and password = 'test';
```
- ![截圖 2022-10-17 下午3 18 17](https://user-images.githubusercontent.com/75289113/196112936-ef3d85e1-5505-4cb2-94a8-bc84162b2b42.png)

### 使⽤ UPDATE 指令更新欄位 username 是 test 的會員資料，將資料中的 name 欄位改成 test2。
```sql
update member set name = 'test2' where username = 'test';
```
- ![截圖 2022-10-17 下午4 34 47](https://user-images.githubusercontent.com/75289113/196129930-07afb2b4-bd81-4797-abb6-63cd4e698ebc.png)


## 要求四
### 取得 member 資料表中，總共有幾筆資料

```sql
select count(*) from member;
```
 - ![截圖 2022-10-17 下午3 56 41](https://user-images.githubusercontent.com/75289113/196120908-dd980594-e1fc-4ed9-97b3-e3630686e985.png)

### 取得 member 資料表中，所有會員 follower_count 欄位的總和。
```sql
select sum(follower_count) from member;
```
- ![截圖 2022-10-17 下午3 58 41](https://user-images.githubusercontent.com/75289113/196121314-ea3d73cb-ff34-4f8d-a730-d3b6acada95e.png)

### 取得 member 資料表中，所有會員 follower_count 欄位的平均數。
```sql
select avg(follower_count) from member;
```
- ![截圖 2022-10-17 下午3 59 47](https://user-images.githubusercontent.com/75289113/196121540-299565b2-3e0f-4794-bec3-9ce0717d8a00.png)

## 要求五
### 建立新資料表紀錄留⾔資訊，取名字為 message。
- ![截圖 2022-10-17 下午4 12 02](https://user-images.githubusercontent.com/75289113/196124004-3e8aded8-28d4-407e-a3ab-8a750cabd863.png)
- ![截圖 2022-10-17 下午4 12 22](https://user-images.githubusercontent.com/75289113/196124053-dfc4a59a-5b90-4f00-b799-a858a947f1ab.png)

### 使⽤ SELECT 搭配 JOIN 語法，取得所有留⾔，結果須包含留⾔者會員的姓名。
```sql
 select member.name , message.content from message inner join member on message.member_id = member.id;
```
- ![截圖 2022-10-17 下午4 36 37](https://user-images.githubusercontent.com/75289113/196130345-8ebe23c0-7f5a-40ee-9f54-bc7fba77ec06.png)


### 使⽤ SELECT 搭配 JOIN 語法，取得 member 資料表中欄位 username 是 test 的所有留⾔，資料中須包含留⾔者會員的姓名。
```sql
select member.name , message.content from message inner join member on message.member_id = member.id where member.username = 'test';
```
- ![截圖 2022-10-17 下午4 38 06](https://user-images.githubusercontent.com/75289113/196130643-c00982b5-c8bc-4785-bbaa-ade43e275754.png)

### 取得 member 資料表中欄位 username 是 test 的所有留⾔平均按讚數。
```sql
select member.username , avg(message.like_count) from message inner join member on message.member_id = member.id where member.username = 'test';
```
- ![截圖 2022-10-17 下午4 43 31](https://user-images.githubusercontent.com/75289113/196131854-e41acb86-7582-437e-bf99-91860a7e3f7d.png)

