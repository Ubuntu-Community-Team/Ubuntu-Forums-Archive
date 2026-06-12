---
title: "How do I start postmaster in PostgreSQL?"
date: 2011-07-07
forum: General Help
---

### Post by New00Folder on 2011-07-07
I just installed PostgreSQL 8.4 from the maverick-updates repository and I've not messed up the default configuration files.

I started a server using pgAdminIII and created a small trial database. Now I want to access this database from a Java program using JDBC (which I've already installed).
I learned that for that I'd have to run a service called postmaster. I read up some reference material which recommend setting PGDATA=/usr/local/pgsql/data and PGLIB=/usr/local/pgsql/lib and adding /usr/local/pgsql/bin to PATH.

/usr/local/pgsql/bin doesn't exist. But I found a corresponding directory /usr/lib/postgresql/8.4/bin which when added to path allows me run "pg_ctl start" or "postmaster" from bash.

Command "pg_ctl start" or "postmaster" now gave an error reporting that PGDATA was unset. Since /usr/local/pgsql/data doesn't exist I set PGDATA=/usr/lib/postgresql/8.4.
Then the commands gave an error about not being able to find "postgresql.conf" in /usr/lib/postgresql/8.4.
I found this file in /etc/postgresql/8.4/main/.

But by now I'm pretty scared of ruining my setup with unnecessary fiddling. I've set PGDATA to blank and I guess I'm back where I started.

Has anyone been through this before? What do I do now?
I don't want to read hundreds of pages of documents 'coz I'm focusing on learning Java and I don't trust them eihter coz they refer to /usr/local/pgsql.

---

### Post by SeijiSensei on 2011-07-07
I'm guessing the documentation to which you're referring came from the JDBC docs; it's both out-of-date and only applicable to PG installations built from source.  There's no longer a postmaster process in 8.4.  If you start PG using the default installation, you'll see a process like this using "ps ax":

```
/usr/lib/postgresql/8.4/bin/postgres -D /var/lib/postgresql/8.4/main -c config_file=/etc/postgresql/8.4/main/postgresql.conf
```

plus four sub-processes all of which are also listed as running "postgres".  The initial process is the equivalent of what was called "postmaster" in earlier versions.

The /usr/local/pgsql stuff only applies if you compile PG from source.  The locations for PostgreSQL on Ubuntu don't use /usr/local at all.

Your original setup was just fine.  You just need to adapt to the locations Ubuntu uses in your Java app.  PGDATA = /var/lib/postgresql/8.4/main.  The binaries like the psql command-line client all live in /usr/bin like any other normal user programs in Ubuntu.  The server binaries are in /usr/lib/postgresql/8.4.  postgresql.conf and other key configuration files like pg_hba.conf reside in /etc/postgresql/8.4/main.

(I'll just mention in passing that if you were running this application on a RedHat-flavored system, you'd have an entirely different set of directories to contend with.)

When you install a server package like PostgreSQL, Ubuntu sets it up to start automatically at boot.  You don't need to do anything else to insure it will begin running at boot.

---

### Post by New00Folder on 2011-07-07
Thanks a lot SeijiSensei.

Now all I'd have to do is to add location of JDBC .jar files to CLASSPATH. Isn't it?

Do I add all three of them or just the last one?
```
/usr/share/java/postgresql-jdbc3-8.4.jar
/usr/share/java/postgresql-jdbc3.jar
/usr/share/java/postgresql.jar
```Or would that be unnecessary 'coz I installed libpg-java from the repo too?

But ```
try {
      Class.forName("org.postgresql.Driver");
    } catch(Exception e) {
      // your error handling code goes here
    }
``` is still throwing ClassNotFoundException. What else do I need to do to make this work?

---

### Post by New00Folder on 2011-07-07
I've sorted it out.
I use NetBeans IDE. Right clicking on libraries gives an option to add a jar file to library. I added /usr/share/java/postgresql.jar to my library and things are working now.

I don't know how to do it without netbeans though.

---

