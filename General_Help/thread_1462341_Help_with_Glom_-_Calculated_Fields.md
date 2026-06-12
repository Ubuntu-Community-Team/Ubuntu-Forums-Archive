---
title: "Help with Glom - Calculated Fields"
date: 2010-04-25
forum: General Help
---

### Post by dsnettleton on 2010-04-25
I operate a small business and would have decided to build a database to handle my customers and finances. After looking through several different types of software, Glom is my favorite; I found it in the Ubuntu Software Center and it does everything I need it to do, but keeps things simple.

My problem is that Glom has one weakness: documentation. Because of the niche nature of the software, I've been having trouble finding tutorials or even forum posts to answer my questions, and Glom's own help pages are incomplete. Which leads me to my actual question.

How do I us the calculated fields in Glom? I've used php with mySQL, and I'm familiar with python script, but the actual implementation into the glom software baffles me.  I just need to run basic search and input queries in the fields, and I believe one of my problems is that I don't know how to set the "Triggered By" field that displays when I edit a calculated field. In other words, I can type simply
```
return 1 + 2
```
and I still get no output in the table fields. Can anyone point me to an in-depth tutorial on this issue, or at least give me a brief overview of what I'm doing wrong?

Thanks,
--D. Scott Nettleton

---

### Post by alexfish on 2010-04-25
HI
don't know if you have look at the examples 


sometimes the examples can't be found after installation

 look through your menus / places you may see a folder there named Examples or you can create a link to the example files .should be in


 usr/share/glom/doc/examples  

when found double click on a  file , then give it a new name so not to get confused, 

have a look at example small buisness

from looking at the field definition values, calculating 2 fields looks something like this

return record["price_total"] + record["vat_total"];

is this of any help

regards

alexfish

---

### Post by dsnettleton on 2010-04-25
Thanks for the reply, but it actually doesn't answer my question.

I have looked at the examples and they use 'related tables.' These are useful and more efficient for some purposes but less versatile than an actual sql query. What I want to know is how to interface with the record.connection to retrieve specific fields from specific tables in the database.

Thanks.

---

### Post by alexfish on 2010-04-25
hi

I am find it hard to grasp what you are trying to achieve

are you trying to valuate certain columns in a given row given that one of the columns is the calculating field , also where there could be a column with an input , say like if a 

Product "box" : Size" A*B*C" : QTY "3 ": COST "12 " : Total = the evaluation of the Size *3*12
Product "Sheet" : Size" A*B" : QTY "4 ": COST "15 "Total = the evaluation of the Size *4*15
and also the Product size can be altered to say box : Size A*B*C / 20

if not, can you explain or give a screen shot of what you are trying to achieve

regards

alexfish

---

### Post by dsnettleton on 2010-04-25
Sorry for the confusion.

In SQL, queries are often submitted using a form such as:
```
SELECT * FROM table_1 WHERE fld_ID = table_2.fld_index
```
These queries are very versatile and allow for multiple variables, and seclusion of particular values.
In PHP, the data is then accessed by a process like:
```
$result=mysql_query($thisQuery);
while ($row=mysql_fetch_assoc($result)) {
     $var1=$row['fld_ID'];
     $var2=$row['fld_title'];
}
```
Notice that using this method, each field can be accessed by name because I have direct access to the database without all the mucking about in a GUI to produce "related tables" like in Glom. I know that Glom allows python scripting that should enable users to access the database in a similar manner. The closest thing I've found to what I'm trying to accomplish is at the bottom of this Gnome documentation page:
[http://library.gnome.org/users/glom/unstable/sec-calculated-fields.html.en]("http://library.gnome.org/users/glom/unstable/sec-calculated-fields.html.en")
Unfortunately, I've struggled with the actual implementation to reconcile what I know about accessing SQL databases in PHP with their python scripting counterparts. The code in the link refers to the data it has retrieved by row and column; that's fine if you want to display a spreadsheet, but I want to be able to select the individual fields by name. I know there's an easy way to do this that I just don't understand and once it's clarified for me, I don't expect to have further troubles.

Thanks for your patience,
--D. Scott Nettleton

---

### Post by dsnettleton on 2010-04-26
Bump

---

### Post by alexfish on 2010-04-30
Hi

I have used Glom in the past , and there can be limitations using the Standard interface

to this end the best i can do is point you here . hope it is of some help


[http://wiki.python.org/moin/DatabaseProgramming/](http://wiki.python.org/moin/DatabaseProgramming/)


Main site

**[[IMG]http://1.2.3.10/bmi/www.python.org/images/python-logo.gif[/IMG]]("http://www.python.org/")**

---

