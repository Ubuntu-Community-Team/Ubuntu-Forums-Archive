---
title: "'   key on keyboard?   trying to create user in MYSQL"
date: 2010-10-28
forum: General Help
---

### Post by spindler on 2010-10-28
I have a weird problem.

I am attempting to create a user in MYSQL. This is my code.

mysql --user=root -p
password: ************

mysql> create user 'bob'@'localhost' identified by '******';

I get an error every time that looks like this.

ERROR 1064(42000): You have an error in your SQL syntax: check the manual that corresponds to your MySQL server version for the right syntax to use near '?bob'@'localhost'' at line 1.

I think the problem is related to my keyboard somehow.   The thing is in order to enter the command in the first place I must  click on the '  key twice for the character to appear.  Of course when I only press the key once I am hoping to see the correct command however the command in the terminal looks like this.

mysql> create user bob@localhost identified by ******;

which gives me a completely different problem.....the system does not put me back into the msql command line.  It looks like this.

mysql> create user bob@localhost identified by ****;
         > grant all privileges on *.* to chris@localhost
         >with grant option;
         >
         >
         >

I just cannot return to the MySQL command line.   I think maybe the Ubuntu system does not like my keyboard and does something funny with the ' key.

Questions:

1. Has anyone seen this issue before?   Anyone know how to fix this?

2. How can I create a user in MySQL?   Is there a different way of doing it?...maybe without using a command line?

---

### Post by TeoBigusGeekus on 2010-10-28
Try mysql administrator, it's in the software center I think. It solves many issues on handling dbs painlessly.

---

### Post by spindler on 2010-10-29
Thank you very much for your help.  It was helpful.

On another note.  I noticed that the `key is kind of funny.  I actually need to press the `key and the space bar for the right character to be entered. 

Who would have guessed.

---

