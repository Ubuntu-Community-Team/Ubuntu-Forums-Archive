---
title: "can't create a document in my var/www folder..."
date: 2010-01-10
forum: General Help
---

### Post by fudgewindows on 2010-01-10
just installed apache and am having some issues. everything works great in regards to LAMP....now....

i can create documents with the terminal using gedit, however, i can not right click inside my www folder and create documents there....

i do not want to have to use the terminal just to add files to my apache www folder.

i have put myself in the "root" user group, and still cannot right click inside the folder to add documents.

i am a ubuntu newb so the solution is more than likely quite simple. any help would be greatly appreciated because using the terminal for everything is a pain in the bottom.

---

### Post by spiderbatdad on 2010-01-10
Launch nautilus as root
```
gksu nautilus
```
You can create a launcher for yourself to run nautilus this way...you will still need passwd

---

### Post by fudgewindows on 2010-01-10
Thanks spider, are there any other workarounds? Or will I always need to enter my PW?

---

### Post by ttoilleb on 2010-01-10
I ddidn't use a www direcctory, I Left everything as subdirectories of /opt/lampp/htdocs, but that doesn't solve yor problem.

First,  
```
gksu nautilus
```
then navigate to /opt/lampp/etc and edit module httpd.conf.  Scroll down a little looking for the followinng lines
```

User nobody
Group nogroup

```

Change them to
```

User <Your Userid>
Group root

```

You could have done gksu gedit /opt/lampp/etc/httpd.conf, but using nautilus bypasses typos.

Now in terminal do
```

 sudo chown +R <type your userid here> <enter full path to your www direcctory here>

```
 
On my system, I entered - sudo chown +R notmyrealuserid /opt/lampp/htdocs - yes, I left everything as subdirecctories of htdocs.

And yes, I know this is not the recomended way of doing this, security and all that.  But this is the way I have my Lampp set and it works just fine for me.

Also channge the /opt/lampp/tmp directory.

The reason for this change - the lines in httpd.conf tell lampp (apache) to switch user after startup.  This cause the ownership of www to be changed.  This appears to be a one time change.  Therefor the need to manually change them again.

---

### Post by lyall on 2010-01-10
you could use chmod on the directory so that you can read/ write to the files in that directory

be careful using chmod, please read up on it before you make any changes.
see the following link for info about chmod
[http://catcode.com/teachmod/]("http://catcode.com/teachmod/")

are you the only user on the PC/Laptop, if so you should have any problems.  If other users are using it you will have check their permissions if they are to use that directory  too.

I hope this helps you

good luck and have fun learning

---

### Post by spiderbatdad on 2010-01-11
> **fudgewindows said:**
> Thanks spider, are there any other workarounds? Or will I always need to enter my PW?

Apache can look where ever you tell it to look for the root document...this is generally configured in /etc/apache2/sites-available/default...or <yoursite>. You can change the document root to /home/<your username>/var/www. Place your index.html, or index files there.
I wrote this a couple of years ago, when I first set up apache at home:
[http://spiderbatdad.wordpress.com/basic-apache2-how-to/](http://spiderbatdad.wordpress.com/basic-apache2-how-to/)

---

### Post by Warren Watts on 2010-01-11
> **spiderbatdad said:**
> Apache can look where ever you tell it to look for the root document...this is generally configured in /etc/apache2/sites-available/default...or <yoursite>. You can change the document root to /home/<your username>/var/www. Place your index.html, or index files there.

My solution was to create a www directory in my home folder and then create a symbolic link in the /var/www folder that points to the www folder in my home folder.

---

