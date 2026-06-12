---
title: "problem with firefox php"
date: 2009-08-24
forum: General Help
---

### Post by phillip1882 on 2009-08-24
when i try to run php script with firefox, it asks me to either browse for file to open with or save file.
even after reading the page on this problem and implementing the "solution" i've hit another snag. i can't place files in the var/www directory as its in my file system which i'm denied access to by ubuntu. any help would be appreciated.

---

### Post by credobyte on 2009-08-24
Open Terminal and paste in this command - it'll fire up Nautilus with root privileges:
```
gksudo nautilus /var/www &

```

---

### Post by PeEllAvaj on 2009-08-24
Perhaps I'm not understanding your problem, but Firefox (or Chrome or IE) can't run PHP.  In order for you to run a PHP script you have made, you need to have a web server like apache installed.

sudo apt-get install apache2

After you have installed apache, then you put the PHP files you want to run into /var/www/ and then browse to them not with file:/// but with [http://localhost/](http://localhost/) in firefox.

Is this what you were trying to accomplish, or was it something else?

---

### Post by Linux&amp;Gsus on 2009-08-24
And if you install Apache only it still wont do it. You also need to install PHP.
> sudo apt-get install php5
Plus potentially other packages, depending on the specific needs.
While we're at it, what are you doing with PHP without a database? If you don't need a database can you not do the same with HTML and CSS only? Your browser will be served with HTML, anyways. The server is handling the PHP.

---

### Post by credobyte on 2009-08-24
> **Linux&Gsus said:**
> And if you install Apache only it still wont do it. You also need to install PHP.

Plus potentially other packages, depending on the specific needs.
While we're at it, what are you doing with PHP without a database? If you don't need a database can you not do the same with HTML and CSS only? Your browser will be served with HTML, anyways. The server is handling the PHP.

What ? PHP is useless if you don't need to deal with databases ? :neutral:

---

### Post by Linux&amp;Gsus on 2009-08-24
> **credobyte said:**
> What ? PHP is useless if you don't need to deal with databases ? :neutral:

Please don't interpret anything into my words that I didn't say.
I didn't say it's useless without a database. I was simply asking what the goal is and if it can be done without PHP. Not more not less.

My comment might or might not have been a bit short on some parts. E.g. that the server could be the desktop/laptop itself while learning/developing, not necessarily another computer. But never did I say PHP is useless without a database.

---

### Post by madnessjack on 2009-08-24
> **credobyte said:**
> What ? PHP is useless if you don't need to deal with databases ? :neutral:
I use it all the time for templates. Don't use the database for that ;-)

---

### Post by 3rdalbum on 2009-08-24
> **phillip1882 said:**
> i can't place files in the var/www directory as its in my file system which i'm denied access to by ubuntu. any help would be appreciated.

Technically, it's not "your" filesystem; it's Root's filesystem. When you log into Ubuntu, you log in as a user. For the protection of the system and other users, when you are a normal user you can't modify anything outside your home directory.

In order to put files into the /var/www directory, you need to temporarily switch to Root. The easiest way is to install the "nautilus-gksu" package, log out and log in again, and then navigate to the /var directory. Right-click on "www" and choose "Open as Administrator".

This command opens up a new instance of the file manager, this time run as Root, so you can do whatever you want to do within the confines of that window.

The command given to you by credobyte does pretty much the same thing:

```
gksudo nautilus /var/www
```

The "gksudo" bit says "Run the rest of this command as root, if the user can authenticate themselves". Nautilus is the name of the file browser, and /var/www is a piece of data you are providing to Nautilus - namely, what folder you want it to open.

---

### Post by credobyte on 2009-08-24
> **Linux&Gsus said:**
> Please don't interpret anything into my words that I didn't say.
I didn't say it's useless without a database. I was simply asking what the goal is and if it can be done without PHP. Not more not less.

My comment might or might not have been a bit short on some parts. E.g. that the server could be the desktop/laptop itself while learning/developing, not necessarily another computer. But never did I say PHP is useless without a database.

> **Linux&Gsus said:**
> And if you install Apache only it still wont do it. You also need to install PHP.

Plus potentially other packages, depending on the specific needs.
While we're at it, **what are you doing with PHP without a database? If you don't need a database can you not do the same with HTML and CSS only?** Your browser will be served with HTML, anyways. The server is handling the PHP.

Did I missed something ? :)

---

### Post by Linux&amp;Gsus on 2009-08-24
> **credobyte said:**
> Did I missed something ? :)
Yes.
And because this discussion is hardly helpful to the OP I wont comment on that any further.

@OP
Follow the advise already given and you'll most likely get the results you need.

---

