---
title: "SQL Question"
date: 2009-07-24
forum: General Help
---

### Post by CrusaderAD on 2009-07-24
Ok, here's my situation:

I'm trying to run a sql statement that pulls only certain data like so:

```
SELECT     COUNT(o.orderID) AS Expr1
FROM         orderdetail AS od 
INNER JOIN  orders AS o ON od.orderID = o.orderID
INNER JOIN  shippingaddresses AS sa ON o.profileID = sa.customerid
INNER JOIN  excelimport1top200 AS ex ON od.productID = ex.ProductID
WHERE     (sa.state = 'CA') AND (o.dateoforder > { fn NOW() } - 365)
```

What I'm trying to do is pull and count orders that ONLY have products in excelimport1top200. So if an order has a product from excelimport1top200 and one product that isn't in that table, I don't want to pull it. How would I do that?

---

### Post by TeoBigusGeekus on 2009-07-24
Could you please give us the layout of the tables mentioned in your query?

EDIT:
Even better, could you post the whole database? (As an .sql file)

---

### Post by gunksta on 2009-07-24
It would be useful to have the full data structure, but probably not absolutely necessary in this instance. But, it would be nice to know what RDBMS you are using. 

I usually write queries against postgres or MS SQL Server. Strict ANSI SQL would be nice, but it seems like using the extensions can often make life easier . . . . and I'm inherently lazy. I'll write something that should work in Postgres. If you're using something else you may have to fiddle with the syntax a little to make it work for you. It's also possible that some of my ideas/syntax may clash with some of your data structures, since I don't actually know what they are. Thus, you will need to read this carefull before trying to use it and it may need some adjusting  to really fit your needs.

First things first. I would break this bad boy up. Why? Because it makes things MUCH easier to look at and think about. Use views. They are your friend. We will make a couple of views, which are basically stored queries. We can then easily write a SIMPLE query against the final view that can answer your final question. This isn't an exercise in Perl obfuscation, so there's no reason to do it all in one shot. This is especially true if you are still learning SQL.

I would start by making an order view. We'll call it allOrders for sake of argument. Note that I am not touching the excelimport1top200 table and I am not touching the shipping table yet either. I'm ignoring the excelimport table because it is not relevant to the actual individual order. I'm ignoring the shipping info because you don't seem to really need the info until later. Doing it this way WILL make the query run faster, which dependent on the size of the database and the horsepower of your computer may or may not be important.

```

CREATE OR REPLACE VIEW allOrders AS
    SELECT *
    FROM orderdetail AS od INNER JOIN  orders AS o ON od.orderID = o.orderID
    WHERE (dateoforder > current_date - 365) ; 

```This will give us a nice list of all the orders that were filed in the last year. I did not include the shipping info, because we don't need it yet and doing that join, knowing that I will drop many of them is a waste of resources at this point.

```

CREATE OR REPLACE VIEW selectOrders AS
    SELECT * FROM allOrders
    WHERE productID IN (SELECT productID FROM excelimport1top200)

    EXCEPT

    SELECT * FROM allOrders 
    WHERE productID NOT IN (SELECT productID FROM excelimport1top200) ;

```A little subquery action goes a long way to making this easy to do. If you want to make the final query run faster, you could make the RDBMS make a table (or even a temporary table) here rather than a view. Your choice.

This query _may_ give us a list of all orders where at least one item is in the excel table but excludes any order where it is not in excel table. But, I don't really know how your data structure. If it's a well structured data set, this SHOULD be a relational view stucture and this will work. If it's some kind of a long string format, this will take ALOT more work and I'd bag of the project if I were you.

Assuming that orderdetails is a relational view, allowing a row to row matching of productID, then we are ready for our final query.

```

SELECT *
FROM  selectOrders AS so LEFT JOIN shippingaddresses AS sa ON so.profileID = sa.customerID 
WHERE state LIKE 'CA'  ;

```I used a left join rather than an inner join in this query because I DON't want to assume that all orders have addresses. They should, but I don't like to assume things.

Look these ideas over and tell me what you think.

---

### Post by oldfred on 2009-07-24
It has been a while but I think you have to join to another query that selects orders based only on orders with no products in top100 table. I would first create that query as a stand alone query to test then combine the logic to make it work.

---

### Post by gunksta on 2009-07-24
> **oldfred said:**
> It has been a while but I think you have to join to another query that selects orders based only on orders with no products in top100 table. I would first create that query as a stand alone query to test then combine the logic to make it work.


That is, in essence what selectOrders view does. It looks simple, but it's actually pretty sneaky. First it creates a list of orders that have a product id in the excel table list. Then it creates a list of orders that have a product id that is not in the excel table list. It then subtracts the second set from the first set, leaving you (ideally) with exactly what the OP wants.

Unfortunately, I can't really test my idea, since I don't have the structure/data to do it with.

---

### Post by CrusaderAD on 2009-07-27
I have one more sql question. I figured I'd just drop it here in this thread:

I have a table with data like this:

Row 1: type = 'A' order = '123' result = 0
Row 2: type = 'D' order = '123' result = 0
Row 3: type = 'A' order = '1234' result = 0
Row 4: type = 'D' order = '1234' result = 11
Row 1: type = 'A' order = '12345' result = 0

Can you pull data all at one time where A doesn't have a corresponding D (so A is alone) and where D doesn't have a result of 0 but has a corresponding A with a result of 0? I know that kinda messed up.

---

### Post by DaithiF on 2009-07-27
like this?

```
drop table if exists sometable;
create table  sometable
(
    type char(1),
    orderid  char(10),
    result int
);

insert into sometable ( type, orderid, result) values
    ( 'A', '123', 0 ),
    ( 'D', '123', 0 ),
    ( 'A', '1234', 0 ),
    ( 'D', '1234', 11 ),
    ( 'A', '12345', 0 );

select a.orderid, a.type, a.result
from sometable a
where (a.type = 'A' and a.orderid not in ( select orderid from sometable where type = 'D' ) )

union

select a.orderid, a.type, a.result
from sometable a, sometable b
where a.type = 'D' and a.result != 0 and a.orderid = b.orderid and b.type = 'A' and b.result = 0;


```
RESULTS
======
orderid type    result
12345   A       0
1234    D       11

---

