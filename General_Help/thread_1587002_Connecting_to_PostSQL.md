---
title: "Connecting to PostSQL"
date: 2010-10-02
forum: General Help
---

### Post by kolo-01 on 2010-10-02
hi,
i think i'm some of the way there to connecting to PostgresSQL- i dont know what it is or what it does but it is required for another program that i want to run. anyway when i run the program i get the error: "unable to connect to this database, please check the configuration". i am not entirely sure what the problem is and this might be a bigger problem than i am capable of dealing with right now as my skills in operating the terminal are not that great. so i have set up a new user and password by the terminal which im pretty sure i have done correctly, it seems though that the problem might be a basic connection problem which somebody may know how to solve quite easily though, so thought i'd put this one out, hope you can help, thanks

---

### Post by SeijiSensei on 2010-10-02
Did you install the postgresql-8.4 package (the PostgreSQL server)?  Is it running?  Did you or the application you're using create the database(s) you need?  What kind of application is it?

If the documentation for this application doesn't provide information on how to set up Postgres, you're facing a serious learning curve before you can use the app.  You might want to start with this: [https://help.ubuntu.com/8.04/serverguide/C/postgresql.html](https://help.ubuntu.com/8.04/serverguide/C/postgresql.html)

---

