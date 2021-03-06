# assignment_data_modeling
Mmmmm.... dataaaaa....

*Include your ERM modeling "pseudocode" in the space below*

## Basic 
### Course
#### Goals
Show all available courses. 
On each course page, display all lessons for that course along with the course description.

#### Entities
- Courses
- Lessons

#### Relationships
This is a one-to-many relationship: A course may have many lessons, but each lesson can only have one course. 

#### Data Models
**Courses:**   

|Column| courseID | title | description  
|:--|:--|:--|:-- |
|**Type** | integer | string | string |
| **Other** | primary key |  |  |


**Lessons:**

| Column | lesson_id | title | description | course_id| 
|:--|:--|:--|:--|:--|
| **Type**  | integer | string | string | integer |
| **Other** | primary key |  |  |   foreign key |


### Profiles
#### Goals
Display a user's demographic information like city, state, country, age and gender. 

#### Entities
- User
- Profile
- Country
- City 

#### Relationships

- One-to-one relationship for User <-> Profile
- One-to-one relationship for City <-> Profile
- One-to-many relationship for Country -> City

#### Data Model

**User Table:**

| Column | user_id | username | email | profile_id  |
|:--|:--|:--|:--|:--|
| **Type**| integer | string | string | integer  |
|**Other** | primary key |  |  | foreign key |

**Profile Table** 

| Column | profile_id | first_name | last_name | city_id | gender | age 
|:--|:--|:--|:--|:--|:--|:--|:--|
| **Type** | integer | string | string | integer | string | integer |  
| **Other** | primary key |  |  |  |  |  |  

**Country Table:**

| Column | country_id | country_name |
|:--|:--|:--|
| **Type** | integer | string |
| **Other** | primary key |  |   

**City Table:**  

| Column | city_id | city_name | city_state | country_id
|:--|:--|:--|:--|:--|
| **Type** | integer | string | string | integer |
| **Other** | primary key | | | foreign key|  


## Intermediate

### Goals

Show multiple posts on a single page, along with the author of the post and the date created. 

On each 'post' page, show the comments and their sub-comments.

### Relationships
Relationships between the tables:   

- One to many for User -> Post  
- One to many for Comment -> Replies  
- One to many for Post -> Comments  

### Entities
- User  
- Post    
- Comment  

### Data Model

**User Table**

| Column | user_id | username | email 
|:--|:--|:--|:--|
| **Type** | integer | string | string |
| **Other** | primary key | | |


**Post Table**

| Column | post_id | title | url | author_id |
|:--|:--|:--|:--|:--|
| Type | integer | string | string | integer|
| Other | primary key |  |  | |

**Comment Table**

|  Column | comment_id | body | author_id  | post_id | parent_comment_id
|:--|:--|:--|:--| :--| :-- |
| Type | integer |  string | integer | integer  | integer (if applicable) |
| Other | primary key |   | foreign key | foreign key| foreign key|


## Advanced
### E-Commerce Site
#### Goals
Build an e-commerce site. Keep track of products, users, orders, shipments. 

#### Entities
- Users
- Products
- Orders
- Shipments


#### Relationships
-  One-to-many for Users -> Orders
-  One-to-many for Orders -> Shipments (an order might be split into many shipments)
-  Many-to-many for Orders <-> Products

#### Data Models

**Users**

| Column | user_id | first_name | last_name | email |
|:--|:--|:--|:--|:--|
| Type | integer | string | string | string |
| Other | primary key  |  |  |  |

**Products**

| Column | product_id | product_name | quantity | ...|
|:--|:--|:--|:--|:--|
| Type | integer | string | integer | ...|
| Other | primary key  |  |  |  |

**Order Table**

| Column | order_id | user_id | ... |  
|:--|:--|:--|:--|:--|
| Type | integer | integer |  |  
| Other | primary key | foreign key |  |  

**Shipment Table**

| Column | shipment_id | order_id | shipment_status_id | shipment_address | ... |
|:--|:--|:--|:--|:--| :-- |
| Type |  int | int | int | string | |
| Other | primary key | foreign key | foreign key |  | |

**OrderProduct Join Table**

| Column | product_id | order_id | quantity |
|:--|:--|:--|:--|
| Type | integer | integer | integer |
| Other | foreign key | foreign key |  |

**ShipmentStatus Table**

| Column | status_id | status_title | status_description |
|:--|:--|:--|:--|
| Type | integer | string | string |
| Other | primary key |  |  |

If a user deletes his/ her account, we might keep the user_id (or row in the table) but delete all personal information related to that account. 

This could mean splitting a User account into three tables: One, User, just for the user_id, another, Profile, for all personal details associated with a user_id, and a third UserProfile Join table. 



Yi-Xuan Lau