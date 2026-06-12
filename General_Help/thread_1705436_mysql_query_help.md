---
title: "mysql query help"
date: 2011-03-12
forum: General Help
---

### Post by ronald.higgins on 2011-03-12
Greets peeps, need an assist with a MySQL query updating with the sum of 2 columns.

TABLE1=Name,Age
TABLE2=Name,Age

What i want to do is update TABLE1.Age withe the combined value of TABLE1.Age & TABLE2.Age but cant seem to get it right?

Thought it would have been something along the lines of:

update TABLE1 set Age= sum(TABLE1.Age + Table2.Age) where Name='x';

But that gives a:

ERROR 1111 (HY000): Invalid use of group function

---

### Post by tordeu on 2011-03-12
In the update part you need to list all tables that you are using and you do not need sum. Sum is used, for example, to add all the values of a specific row.

In your case you want something like this:

```

UPDATE TABLE1, TABLE2 
SET TABLE1.Age=TABLE1.Age+TABLE2.Age 
WHERE TABLE1.Name='x' AND TABLE2.Name='x'; 

```

---

### Post by ronald.higgins on 2011-03-12
Thanks for the assist tordeu! Much appreciated.

But alas, in trying to simplify the issue as much as possible I have skewered the scenario.

I have a variable set in a script being passed down to the SQL Query and need to pull that into the update so SUM will need to be used?

######
DIFF=3

update TABLE1 set Age= sum(TABLE1.Age + $DIFF) where Name='x';
######

---

### Post by tordeu on 2011-03-12
No, you don't need sum for that. You can just do

```

update TABLE1 set Age= Age + $DIFF where Name='x';

```You only need sum if you have a table like this:

```

[FONT=Courier New]Name   Age
----   ---
x      20
y      38
z      40[/FONT]

```And you want to add all the ages (so, 20+38+40), which would be done with SUM(Age) (which means SUM all values in the Age Column). To just add 3 to a specific age value, you can only to age=age+3.

---

### Post by ronald.higgins on 2011-03-12
thanks very much, that did the trick, thanks again for the assist!

---

### Post by tordeu on 2011-03-12
You're welcome. Just something I forgot:

In your first statement, you did not have to run

```

UPDATE TABLE1, TABLE2 
SET TABLE1.Age=TABLE1.Age+TABLE2.Age 
WHERE TABLE1.Name='x' AND TABLE2.Name='x';

```

for every possible name.

You could do just do:

```

UPDATE TABLE1,TABLE2 SET T1.Age=T1.Age+T2.Age WHERE TABLE1.Name=TABLE2.Name;

```

which would automatically add the all age values from TABLE2 to the appropriate Age values of TABLE1. Depending on what you want to do, maybe this could help you as well.

---

