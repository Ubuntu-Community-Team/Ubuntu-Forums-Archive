---
title: "Password failure for pgadmin3"
date: 2012-03-03
forum: General Help
---

### Post by Mcron on 2012-03-03
New Linux user, love it :)

I installed postgresql, and pgadmin3, then tried to add a server in the pgadmin3 panel.

I added the server (localhost), username and  password.  At this point I have an error

"Error connecting to the server: FATAL:  password authentication failed for user "postgres"
FATAL:  password authentication failed for user "postgres"" 

The username and password should be correct, and I can't find  "./pgpass". 

So... is there a default password ?   Does anyone  know where I can find the password it wants me to use ? Can I change or reset the password ?


Thanks...

---

### Post by Gremlinzzz on 2012-03-03
:popcorn:
[http://www.ubuntugeek.com/howto-setup-database-server-with-postgresql-and-pgadmin3.html](http://www.ubuntugeek.com/howto-setup-database-server-with-postgresql-and-pgadmin3.html)

no experience with them but it mentioned /Now we need to reset the password for the &#8216;postgres&#8217; admin account for the server

---

### Post by Mcron on 2012-03-03
Oh, cool... they give instructions that seems to have broken it more :)   Executing pgadmin from terminal now gets an error rather than a load.  Error; "Unable to initialize gtk, is DISPLAY set properly?"


BUT I'm sure the answer is somewhere on the link you sent. Thanks for the point in the right direction.

---

### Post by negora on 2012-05-08
I don't use the PostgreSQL sever bundled with Ubuntu, but many Linux distributions install it either without setting a password or setting a secret one.

You must type **sudo su - postgres** to gain control over the system's user "postgres". Once you're using its credentials you can change his password in the database using the "psql" command line program, without the need of knowing the previous one.

Why? Because the default configuration file of PostgreSQL (pg_hba.conf) allows the super-administrator connect without specifying his current password.

How to change it? First, you must connect to any existing database (it does not matter which one). For example, type **psql template0** to connect the database "template0".

Second, run this SQL query: ALTER USER postgres WITH ENCRYPTED PASSWORD &#8216;<password>&#8217;;

Where "password" is your new password, obviously.

You may want to remove the "psql" history at your home directory (.psql_history) to avoid that the password is stored there as plain text.

---

