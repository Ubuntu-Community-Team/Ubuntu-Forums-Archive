---
title: "PostgreSQL Daemon"
date: 2011-02-24
forum: General Help
---

### Post by aj00200 on 2011-02-24
While watching the text scroll by as I shut down I noticed that there is a PostgreSQL Daemon running somewhere. The question I have is, how do I add myself and my own database to this daemon or do I need to run one on my own user?

---

### Post by SeijiSensei on 2011-02-24
Easiest solution is to become the postgres user and run the createuser command:

```

$ sudo su
[Enter your password]

# su postgres
$ createuser username

[Answer the questions that follow.  I usually let the new user
create databases but not new accounts.]

$ exit
# exit

```

There should be a pre-existing Linux user named "username" before you create the PostgreSQL user with the same name.  

Now you can run the "createdb" command as that user to create a database you own.

See "man createuser" and "man createdb" for more details.

From the command line, you can use the "psql" client program to talk to the database you created.

---

### Post by aj00200 on 2011-02-24
Thanks, I got your instructions to work and I now have a functional database :)

---

