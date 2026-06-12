---
title: "!! Need help resetting MySQL Root Password."
date: 2011-02-19
forum: General Help
---

### Post by spindler on 2011-02-19
Hello

I have made a big mistake. and I hope someone can help. 

I have a website on my Ubuntu server ( Version 10.04 with a LMAP) I am  having problems accessing my site remotely in order to upload pictures  to the website.  This has been a low priority but long term problem.... I  have posted questions about this issue on this forum without resolving  my problem...so i have been holding off fixing it until I have  time......now I have time...  So I thought it might be worth while to  try something different to fix my problem.   I thought I might create a  directory in the VAR folder to uploads files to directly.....In order to  do this I thought first I need to change the owner of the VAR  director...so this is what I did.


SUDO chown -R root:user var


of course once I did this my website went down!             I saw the following error message using Firefox.

_ERROR establishing a database connection   _

Seeing this issue.  I attempted to correct my mistake and changed the owner back to  root:root using the following:

sudo chown -R  root:root VAR

I thought this would set everything back to normal....However, It did not.             I then attempted the following:

sudo /etc/init.d/apache2 reload
sudo /etc/init.d/apache2 restart

This did not reconnect the database.....So I restarted the server.   During the restart I received two new errors.
[U]
Could not update ICEauthority file var/lib/gdm/iceauthority[/U]

_There is a problem with the configuration server.  (/user/lib/libgconf204/gconf-sanity-check-2 exited with status 256)_


MYSQL ROOT PASSWORD RESET.

I also checked to see if I could log into MySQL and I could not when I used a shell or the Http tool. All of my user names and password do not work. 

 I found a link that should help me reset the root password.  Here is a[ link]("http://http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/").  

So I stopped the MySQL using the following commands and then I came to an error.

sudo /etc/init.d/mysql stop
sudo mysqld --skip-grant-tables &

Then the shell displayed the following:

               user@server: sudo mysqld --skip-grant-tables &
               [1] 6222
              user@server: 110219 11:02:06 [Note] Plugin 'FEDERATED' is disabled.
              110219 11:02:06 InnoDB: Operation system error number 13 is a file operation.
              InnoDB: The error means mysql does not have access rights to
              InnoDB: the directory.
              InnoDB: File name ./ibdatal
              InnoDB: File operation call: 'create'.
              InnobDB Cannot continue operation.

So what is broken?  How can I fix it? 

Please.... any help would be great?

---

### Post by asmoore82 on 2011-02-19
> **spindler said:**
> SUDO chown -R root:user var
…
sudo chown -R  root:root VAR
…
Please.... any help would be great?

This is another simple case of "`sudo …` broke my system!"
This wording is a big problem in general, because sudo does only what it is
told. A more proper phrasing would be "I broke my system using `sudo …`"

There is a ton of stuff in "/var" that should **not** be owned by root.
I would consider backup/re-installation and carefully putting everything back
in place — being mindful of ownership and permissions.

The answer to the thread title is a simple:
```
sudo dpkg-reconfigure mysql-server-5.1
```

---

### Post by spindler on 2011-02-19
Thanks a lot.  This looks like something I am looking for.   Just one thing i am concerned about.   Will I loss all of my data in my database if I reconfigure MySQL using the    dpkg - reconfigure mysql-server-5.1?

Thanks,

Spindler

---

### Post by Habitual on 2011-02-19
no data loss should occur.

just in case run this before you reconfigure:
```
sudo cp -pr /var/lib/mysql /var/lib/mysql.org
```

---

### Post by spindler on 2011-02-19
OK  what will this do?  

Is there a way I can backup my databases from a folder?   Can I do a copy and paste of the entire MySQL database?

---

### Post by Monotoko on 2011-02-19
That command will back up all of your databases. It copies them into a backup folder.

However, your server will now be rather insecure if everything in var is still owned by root, I would attempt to restore from an earlier backup otherwise you will be attracting hackers and script kiddies, and eventually they may get lucky.

---

### Post by Habitual on 2011-02-19
> **spindler said:**
> OK  what will this do?  

Is there a way I can backup my databases from a folder?   Can I do a copy and paste of the entire MySQL database?

"folders" - We don't use those in Linux. There are **files** and there are **directories**.

/var/lib/mysql is the System directory for the entire mysql database(s)
Look under /var/lib/mysql/* for individual mysql databases.
```
sudo ls -alh /var/lib/mysql/*
``` to see individual DBs.

```
sudo cp -pr /var/lib/mysql ~/mysql.org
``` will copy all of your DBs to your /home directory, but the directory will be owned by root.

Hope this helps.

---

### Post by Habitual on 2011-02-19
> **Monotoko said:**
> ...insecure if everything in var is still owned by root...

Care to elaborate on how that is exactly?
How are root owned files insecure?

---

### Post by spindler on 2011-02-19
This is very helpful.  I am not sure if I did a recent enough backup of the entire server.  Does Ubuntu Linux do a backup automatically at some time?   Is there a way I can find out?  Where would I look?

Thanks,

Spindler

---

### Post by spindler on 2011-02-19
Is there a way I can view a sample of what the VAR directory is suppose to look like?  Maybe I can just chown the directories individually and put everything back the way it should be?  

Can someone provide me a directory tree of the VAR?

Thanks,

Spindler

---

### Post by spindler on 2011-02-19
I used the following command to view my database.
sudo cp -pr /var/lib/mysql ~/mysql.org
I received an error.

sudo cp -pr /var/lib/mysql ~/mysql.org

So then I tried to copy my database using the following command.

sudo cp -pr /var/lib/mysql ~/mysql.org
I took a look at the home directory to see if I could find a backup.sql but I did not find anything.  What does it look like? How do I know I created a backup successfully?

---

### Post by spindler on 2011-02-20
Thanks everyone for your help.  i was able to recover MySQL.   I still need to look into fixing the VAR chown issue but at least my website is up again.  :)

Spindler:popcorn:

---

### Post by PaulReaver on 2011-02-20
just incase anyone else has this problem in the future

[http://dev.mysql.com/doc/refman/4.1/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/4.1/en/resetting-permissions.html)

---

