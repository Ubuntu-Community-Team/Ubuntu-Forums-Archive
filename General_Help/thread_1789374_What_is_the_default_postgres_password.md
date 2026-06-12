---
title: "What is the default postgres password?"
date: 2011-06-23
forum: General Help
---

### Post by dslowik2 on 2011-06-23
I just installed postgresql 8.4 package on my Ubuntu 10.10 desktop. Seems to have worked fine. But what is the password for logging into the databases created by user 'postgres'? I can 
sudo su postgres
and then 
createdb
or 
psql mydb
fine and it never asks me for a password. But if I want to use pgadmin3, I want to enter passwd for postgres, etc.

---

### Post by josephmills on 2011-06-23
> **dslowik2 said:**
> I just installed postgresql 8.4 package on my Ubuntu 10.10 desktop. Seems to have worked fine. But what is the password for logging into the databases created by used 'postgres'? I can 
sudo su postgres
and then 
createdb
or 
psql mydb
fine and it never asks me for a password. But if I want to use pgadmin3 to I want to enter passwd for postgres, etc.

did you try root and toor or Admin and toor ?

---

### Post by ratcheer on 2011-07-22
I know this thread is a little old, but in general, you just use the root account to reset the postgres password to whatever you want:

sudo passwd postgres

Tim

---

### Post by SeijiSensei on 2011-07-22
I think he wants to create a password within PostgreSQL, not create a password for the postgres user.

I never give the postgres user a password; I just use su to become the postgres user, do what I need to do, then leave.

If you want to create a password-protected database, first create a PG user by running the "createuser -P username" as the postgres user.  You'll be prompted to create a password.  "username" does not necessarily have to correspond to a system-level user, but if it does not, you may need to play with the permissions in the pg_hba.conf file.  (I routinely edit this file to "trust" connections via localhost.)  

Then configure pgadmin3 to use the username and password you created to manage the database.

---

### Post by DaH-RaT on 2011-08-29
l

---

