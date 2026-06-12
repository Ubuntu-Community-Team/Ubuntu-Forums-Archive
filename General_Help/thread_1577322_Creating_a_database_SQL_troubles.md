---
title: "Creating a database SQL troubles"
date: 2010-09-18
forum: General Help
---

### Post by Kareta on 2010-09-18
Having problem's making a MaNGOS DB.

I need some help regarding to this thread: [http://getmangos.com/community/showthread.php?t=7839](http://getmangos.com/community/showthread.php?t=7839).

Step 6, I don't know what to do. 

[QUOTE=phelpsben][COLOR=darkorange]**Step 6 - Setup the Database**[/COLOR]
There is a magic little command we use during the setup process, this makes things so much simpler.
```
~# mysql -p'YOUR PASSWORD HERE'
```We will use this in place of a Windows/Mac MySQL application.
 
**Create the MaNGOS database**
```
~# mysql -p'YOUR PASSWORD HERE' < mangos/sql/create_mysql.sql
~# mysql -p'YOUR PASSWORD HERE' < ScriptDev2/sql/ScriptDev2_create_database.sql
~# mysql -p'YOUR PASSWORD HERE' ScriptDev2 < ScriptDev2/sql/ScriptDev2_create_structure_mysql.sql
```**Populate the database**
```
~# mysql -p'YOUR PASSWORD HERE' mangos < mangos/sql/mangos.sql
~# mysql -p'YOUR PASSWORD HERE' characters < mangos/sql/characters.sql
~# mysql -p'YOUR PASSWORD HERE' realmd < mangos/sql/realmd.sql
~# mysql -p'YOUR PASSWORD HERE' ScriptDev2 < ScriptDev2/sql/ScriptDev2_script_full.sql
```**World Database**
 
*Download Database*
This is strictly copy/paste for current, this will break in the future, i will try to keep this updated
```
~# wget https://unifieddb.svn.sourceforge.net/svnroot/unifieddb/trunk/Full_DB/UDB_0.11.6_Core_8734_SD2_1480.rar https://sd2-acid.svn.sourceforge.net/svnroot/sd2-acid/trunk/wotlk/3.0.1/3.0.1_acid.sql --no-check-certificate;unrar e UDB*;
```

*Install Database*
```
~# mysql -p'YOUR PASSWORD HERE' mangos < UDB_0.11.6_Core_8734_SD2_1480.sql
~# mysql -p'YOUR PASSWORD HERE' mangos < 3.0.1_acid.sql
~# mysql -p'YOUR PASSWORD HERE' mangos < /mangos/src/bindings/ScriptDev2/sql/mangos_scriptname_full.sql
```
**_Now apply MySQL updates. There is a list right after this post, you can follow it to update._**
 [/quote]

I'm having troubles with: 

```
mysql -p'YOUR PASSWORD HERE' < mangos/sql/create_mysql.sql
```

when I run it without a semicolon, I just get a 
```
 ->
``` when I run it with a semicolon (or do 'show databases;' after) it gives me:

```
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'mysql -u root -p'password' < mangos/sql/create_mysql.sql

```

substituted my password with password.

---

### Post by Ocxic on 2010-09-18
there has to be a space between -p and your password.

---

### Post by bodhi.zazen on 2010-09-18
and your > is on the wrong side of "mangos".

---

### Post by Craig Logan on 2010-09-18
```
mysql -uuser -ppassword < mangos/sql/create_mysql.sql
```

use no space and no quotes.

---

### Post by Kareta on 2010-09-18
> **Ocxic said:**
> there has to be a space between -p and your password.


if I do ```
kareta@ubuntu:~$ mysql -u root -p 'password'
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
``` it gives me that

if I do ```
kareta@ubuntu:~$ mysql -u root -p'password'
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 35
Server version: 5.1.41-3ubuntu12.6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```it let's me in. 

Is my MYsql messed up? 

> **bodhi.zazen said:**
> and your > is on the wrong side of "mangos".

So is it 
```
mysql -p'password' mangos > /sql/create_mysql.sql
```Sorry, I don't know what I'm doing :(.

> **Craig Logan said:**
> ```
mysql -uuser -ppassword <  mangos/sql/create_mysql.sql
```use no space and no quotes.

Thanks, is it supposed to just take me back to ```
~$
```?

---

### Post by Craig Logan on 2010-09-18
chances are it worked if it didn't give you an error message. log in to mysql and check if your databases/tables are there.

---

### Post by Kareta on 2010-09-18
> **Craig Logan said:**
> chances are it worked if it didn't give you an error message. log in to mysql and check if your databases/tables are there.
```

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
+--------------------+
2 rows in set (0.00 sec)

```Is the command supposed to be executed in mysql?

```

mysql -uuser -ppassword <  mangos/sql/create_mysql.sql
```

---

### Post by Craig Logan on 2010-09-18
> Is the command supposed to be executed in mysql?no, execute it from the command line.

please post the contents of create_mysql.sql if this doesn't work.

---

### Post by Kareta on 2010-09-18
> **Craig Logan said:**
> no, execute it from the command line.

please post the contents of create_mysql.sql if this doesn't work.

I did, the chart was show 'databases;' after doing that.


contents of create_mysql.sql:
```
GRANT USAGE ON * . * TO 'mangos'@'localhost' IDENTIFIED BY 'mangos' WITH MAX_QUERIES_PER_HOUR 0 MAX_CONNECTIONS_PER_HOUR 0 MAX_UPDATES_PER_HOUR 0 ;

CREATE DATABASE `mangos` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;

CREATE DATABASE `characters` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;

CREATE DATABASE `realmd` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;

GRANT ALL PRIVILEGES ON `mangos` . * TO 'mangos'@'localhost' WITH GRANT OPTION;

GRANT ALL PRIVILEGES ON `characters` . * TO 'mangos'@'localhost' WITH GRANT OPTION;

GRANT ALL PRIVILEGES ON `realmd` . * TO 'mangos'@'localhost' WITH GRANT OPTION;

```

---

### Post by Craig Logan on 2010-09-18
> I did, the chart was show 'databases;' after doing that.

to be clear, DON'T use the mysql shell to issue that command.

best thing is you open a fresh shell window and put the command I gave you there.

---

### Post by Kareta on 2010-09-18
> **Craig Logan said:**
> to be clear, DON'T use the mysql shell to issue that command.

best thing is you open a fresh shell window and put the command I gave you there.

But to show databases after I've done that in a new shell window, I log in to mysql and use
```
show databases;
```?

Because that's what I did, I executed the command in shell and then logged in to mysql and used 'show databases;'.

I'm a bit confused.

---

### Post by Craig Logan on 2010-09-18
ok, that was correct then.

what's strange is that the databases were not created. it should have worked.

what you can do now is log in to mysql and then copy & paste the sql file into it line by  line and see where exactly mysql throws an error.

---

### Post by Kareta on 2010-09-18
> **Craig Logan said:**
> ok, that was correct then.

what's strange is that the databases were not created. it should have worked.

what you can do now is log in to mysql and then copy & paste the sql file into it line by  line and see where exactly mysql throws an error.
```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 48
Server version: 5.1.41-3ubuntu12.6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> GRANT USAGE ON * . * TO 'mangos'@'localhost' IDENTIFIED BY 'mangos' WITH MAX_QUERIES_PER_HOUR 0 MAX_CONNECTIONS_PER_HOUR 0 MAX_UPDATES_PER_HOUR 0 ;
Query OK, 0 rows affected (0.05 sec)

mysql> CREATE DATABASE `mangos` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
Query OK, 1 row affected (0.01 sec)

mysql> CREATE DATABASE `characters` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
Query OK, 1 row affected (0.01 sec)

mysql> CREATE DATABASE `realmd` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
Query OK, 1 row affected (0.01 sec)

mysql> GRANT ALL PRIVILEGES ON `mangos` . * TO 'mangos'@'localhost' WITH GRANT OPTION;
Query OK, 0 rows affected (0.00 sec)

mysql> GRANT ALL PRIVILEGES ON `characters` . * TO 'mangos'@'localhost' WITH GRANT OPTION;
Query OK, 0 rows affected (0.00 sec)

mysql> GRANT ALL PRIVILEGES ON `realmd` . * TO 'mangos'@'localhost' WITH GRANT OPTION;
Query OK, 0 rows affected (0.00 sec)

mysql> 

```
There's the line-by-line execution.

And now when I 'show databases;' I get

```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| characters         |
| mangos             |
| mysql              |
| realmd             |
+--------------------+
5 rows in set (0.00 sec)

```

Should I do the next step just like i did the first? Line-by-line? Because that seamed to work.

---

### Post by Craig Logan on 2010-09-18
what would be the next step? if there are hundreds of lines to be inserted into the db, you're probably better off investigating why the first command didn't work.

---

### Post by Kareta on 2010-09-18
> **Craig Logan said:**
> what would be the next step? if there are hundreds of lines to be inserted into the db, you're probably better off investigating why the first command didn't work.

This is the next step: 
```

kareta@ubuntu:~$ mysql -uroot -ppassword < ScriptDev2/sql/ScriptDev2_create_database.sql
bash: ScriptDev2/sql/ScriptDev2_create_database.sql: No such file or directory

```
But the file does exist, here are the contents:
```
CREATE DATABASE `scriptdev2` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;

GRANT ALL PRIVILEGES ON `scriptdev2` . * TO 'mangos'@'localhost' WITH GRANT OPTION;
```

(Check the original post's quote for the steps)

---

