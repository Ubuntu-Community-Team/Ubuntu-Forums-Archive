---
title: "MYSQL problems:"
date: 2009-07-02
forum: General Help
---

### Post by buntu_hugenewbie11 on 2009-07-02
I am trying to migrate a db created in Windows (which works fine in Windows) into kubuntu hardy (64 bit)
I installed mySql the following way:

apt-get install mysql-server-5.0

and now when I try to load the sql db I get the following error:
ERROR 1064 (42000): You have an error in your SQL syntax;

This suggests that 5.0 is too old a version.
My problem is that I cannot install a newer version without errors.
I cannot login as root.
Does anyone know a good how-to for setting up mySQL in ubuntu?

---

### Post by credobyte on 2009-07-02
Actually, you should install mysql-server, not mysql-server-5.0 ( packages might be different ).
Haven't saw any problems in using ( exporting/importing/modifying ) SQL files made on Win32 platforms.

---

### Post by The Cog on 2009-07-02
What do you mean by "load the db"? Are you trying to restore an sqldump, or are you trying to run an application that talks to the database?

Note that on Linux, the database and table names are case sensitive whereas they are not on Windows. However, I don't think getting the table or database name would tell you there was an error in your SQL syntax, so I don't think that is your actual problem at the moment.

---

### Post by buntu_hugenewbie11 on 2009-07-02
iam just running mysql
and stating
source 'dbname'.sql
Then I get the above error.
I think it may be because the version in hardy repos is 5.0.51.
Is there an easy way for a newbie to get mySQL5.1 in ubuntu hardy?

---

### Post by The Cog on 2009-07-02
You could try enabling the backports repository and see if it is in there.

I know it's in the Jaunty repos although the default MySQL is still v5.0.

---

### Post by buntu_hugenewbie11 on 2009-07-03
I have the backports available.
Or so I thought....
Is there any other way to get 5.1 for hardy?

---

