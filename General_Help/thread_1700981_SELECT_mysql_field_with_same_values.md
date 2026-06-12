---
title: "SELECT mysql field with same values"
date: 2011-03-05
forum: General Help
---

### Post by Jovenrp on 2011-03-05
How can I select the fields in mysql with the same values inserted?

---------------------------------------------------
id | name | 7:30 am | 8:00 am | 8:30 am | 9:00 am |
---------------------------------------------------
 1 | pan1 |   M     |    M    |   M     |   T     |
---------------------------------------------------
 2 | pan2 |   M     |    M    |   M     |   T     |
---------------------------------------------------
 3 | pan3 |   M     |    M    |   M     |   T     |
---------------------------------------------------

The result of the query should output 7:30 am, 8:00 am, 8:30 am because pan1 all have the same values inserted to that time which is M. Can anyone help me..? Thanks :)

---

### Post by wiggly81 on 2011-03-05
what scripting language are you using i would amuse the answer would differ for different languages

---

### Post by tgm4883 on 2011-03-05
> **Jovenrp said:**
> How can I select the fields in mysql with the same values inserted?

---------------------------------------------------
id | name | 7:30 am | 8:00 am | 8:30 am | 9:00 am |
---------------------------------------------------
 1 | pan1 |   M     |    M    |   M     |   T     |
---------------------------------------------------
 2 | pan2 |   M     |    M    |   M     |   T     |
---------------------------------------------------
 3 | pan3 |   M     |    M    |   M     |   T     |
---------------------------------------------------

The result of the query should output 7:30 am, 8:00 am, 8:30 am because pan1 all have the same values inserted to that time which is M. Can anyone help me..? Thanks :)

I'm confused by what you actually want, and what is in the table. It sounds like you want to print the column name for each value M in each row. If thats the case, i'm not sure how you would do that. It that is the case, it's not a very good way to make the table (IMHO)

---

### Post by Habitual on 2011-03-05
It would REALLY help a LOT if you *show us the query* you say "should" do what you are asking it to do.

Using OR operations (field1 OR field2 OR field3 = M...)
select field1, field2, field3 from table_name where field1 = 'M' or field2 = 'M' or field3 = 'M';

Using AND operations (field1 AND field2 AND field3 = M...)
select field1, field2, field3 from table_name where field1 = 'M' and field2 = 'M' and field3 = 'M';

OR  operation will give f1,f2,f3 if **any** of those fields = M
AND operation will give f1,f2,f3 if ***ALL*** of those fields = M

---

### Post by Jovenrp on 2011-03-06
> **wiggly81 said:**
> what scripting language are you using i would amuse the answer would differ for different languages

I'm using mysql. I'm trying to query the table to output the field_name which is the time.

---

### Post by Jovenrp on 2011-03-06
> **tgm4883 said:**
> I'm confused by what you actually want, and what is in the table. It sounds like you want to print the column name for each value M in each row. If thats the case, i'm not sure how you would do that. It that is the case, it's not a very good way to make the table (IMHO)

Yes, I would like to get the column names which has the values M inserted to it. Is it possible or not? Thanks.

---

### Post by Jovenrp on 2011-03-06
> **Habitual said:**
> It would REALLY help a LOT if you *show us the query* you say "should" do what you are asking it to do.

Using OR operations (field1 OR field2 OR field3 = M...)
select field1, field2, field3 from table_name where field1 = 'M' or field2 = 'M' or field3 = 'M';

Using AND operations (field1 AND field2 AND field3 = M...)
select field1, field2, field3 from table_name where field1 = 'M' and field2 = 'M' and field3 = 'M';

OR  operation will give f1,f2,f3 if **any** of those fields = M
AND operation will give f1,f2,f3 if ***ALL*** of those fields = M

Im trying to get the column_names which has a value of 'M' inserted to it.

the table structure is:

id int auto_increment
name varchar(255)
7:30am varchar(255)
8:00am varchar(255)
8:30am varchar(255)

Thanks.

---

### Post by LoneWolfJack on 2011-03-06
sorry if the following sounds rude.

what you are trying to do is complete nonsense. you don't fetch column names to verify certain data has been stored in a table. in fact, this is so absurd that I would suggest that you put some serious effort into reading up on and at least getting a basic understanding of data normalization before continuing because you apparently have no idea how a RDMS works.

as a solution, remove the time columns from the table. add a second table with columns user_id and time. use the second table to store your times, then query this table.

---

### Post by asmoore82 on 2011-03-06
+1 for LoneWolfJack, also with no rudeness intended.

MySQL is almost always a smaller piece of a much larger puzzle and as such
the querying logic is almost always in another language entirely, Java and PHP
being the most popular. I myself use it with the Django framework in Python.

The hardest thing to do right is great table design.

For Relational Database Systems, *Relational* is the magic work.
If you're *NOT* making sense of the relationships,
it can turn into just a convoluted spreadsheet mess.

---

### Post by Habitual on 2011-03-06
The field names do seem poorly thought out.

---

### Post by wiggly81 on 2011-03-06
I would suggest the best starting point would be to try and explain what the end goal of this project will be, this will make any extra help possible and will give people the chance to actually see what programming language is to be used.

---

### Post by The Cog on 2011-03-06
I don't think that can be done in SQL. Something like this (python) might do it for you though:
```
result = []
for colname in ['7:30 am','8:00 am','8:30 am']:
    cursor.execute("SELECT COUNT(*) FROM table WHERE name = 'pan1' AND `" + colname + "` = 'M'")
    if cursor.fetchone()[0] > 0:
        result.append(colname)
print ", ".join(result)

```
But I hate the column names - are they actually legal?

And I agree the table design looks wrong to me. Something like this might be better:
```

id | name | time | state
1  | pan1 | 0730 | M
1  | pan2 | 0730 | M
3  | pan3 | 0730 | M
4  | pan1 | 0800 | M
5  | pan2 | 0800 | M
6  | pan3 | 0800 | M
7  | pan1 | 0830 | M
8  | pan2 | 0830 | M
9  | pan3 | 0830 | M
10 | pan1 | 0900 | T
11 | pan2 | 0900 | T
12 | pan3 | 0900 | T

```
so you could do something like:
> SELECT time FROM table WHERE name = 'pan1' and state = 'T' ORDER BY  time;
although that will produce the times on separate lines.

---

### Post by tgm4883 on 2011-03-06
I agree, sounds like incorrectly designed tables.

It would seem you have some sort of schedule for different panels in a spreadsheet and have put that into a DB table. That isn't really how you should be doing that. Would need to know more about what exactly you are doing to try and fix it.

---

### Post by Habitual on 2011-03-06
> **The Cog said:**
> But I hate the column names - are they actually legal?


In my mind, a big red flag is the **:** symbol.
9:00AM would be 'better' as 0900 but that begs the Q, 0900 *where?*

Someone wise once said "If you fail to plan, you plan to fail". Goes for MySQL database|table design, logic flow, everything MySQL mandates

---

### Post by Jovenrp on 2011-03-07
Thanks to all! But I already solved the problem.. :D

---

