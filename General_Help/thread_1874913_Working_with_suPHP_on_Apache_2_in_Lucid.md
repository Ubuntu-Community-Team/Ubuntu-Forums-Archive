---
title: "Working with suPHP on Apache 2 in Lucid"
date: 2011-11-04
forum: General Help
---

### Post by moonguide on 2011-11-04
Does anyone have a good site reference for how to work with suPHP on Apache 2?

OS is 10.04.

Using Synaptic, I installed apache2, which brought along apache2.2-common and apache2.2-bin.
The version is 2.2.14-5ubuntu8.6.

Next I installed suphp-common and libapache2-mod-suphp which brought along php5-common and php 5-cgi.
Both suphp packages are version 0.7.1-1. The php5 packages are version 5.3.2-1ubuntu4.10.

If I browse to localhost the "It works!" page opens, showing that Apache is working. If I change the name from index.html to index.php I get the "500 Internal Server Error" error message.

I'm assuming that there must be something different in the way php files are handled, or perhaps there's something else I was supposed to do that doesn't show up in the installation instructions I've read.

Pointers to appropriate documentation are appreciated.

Thanks.

---

### Post by wojox on 2011-11-04
If I remember correctly you have to edit 
```
/etc/apache2/mods-enabled/mime.conf 
```

and then in the AddHandler section
```
AddHandler php5-script .php
```

Then restart Apache.

---

### Post by moonguide on 2011-11-04
> **wojox said:**
> If I remember correctly you have to edit 
```
/etc/apache2/mods-enabled/mime.conf 
```

and then in the AddHandler section
```
AddHandler php5-script .php
```

Then restart Apache.

As it turns out I didn't have to do either of those. Much Googling turned up this answer:

Important clues came from [http://www.develobert.info/2008/04/uid-of-script-is-smaller-than-minuid.html](http://www.develobert.info/2008/04/uid-of-script-is-smaller-than-minuid.html) He states: "The point of suPHP is to make sure scripts are running as the person who owns them."

Another clue came from [http://www.youtube.com/watch?v=qw95e7eWZEw](http://www.youtube.com/watch?v=qw95e7eWZEw) He demonstrates how to change the location of DocumentRoot so that the files are owned by me.

I created a directory www in /home/(*my login name*) and changed the entry in /etc/apache2/sites-available from

DocumentRoot /var/www

to

DocumentRoot /home/(*my login name*)/www

After restarting Apache it now looks at the new directory. To restart Apache open a terminal and type:

sudo /etc/init.d/apache2 restart

The next step is to get suPHP to agree to serve .php files. That requires telling it which directory or directories it is allowed to use. I changed the entry in /etc/suphp/suphp.conf from

;Path all scripts have to be in
docroot=/var/www:${HOME}/public_html

to

;Path all scripts have to be in
docroot=/home/(*my login name*)/www

and then restarted Apache, again.

To test it I added a href to index.html pointing to a simple .php file containing only the following line:

<?php phpinfo(); ?>

The only piece I haven't found, yet, is how to get Apache to recognize index.php as the default file to serve from the directory. I suspect there is another configuration line I need to tweak somewhere.

---

### Post by wojox on 2011-11-04
I'll look tonight, but I think it's in httpd.conf, look for 
```
AddType application/x-httpd-php .php .htm .html
```

---

### Post by moonguide on 2011-11-04
Thanks. 

My httpd.conf was empty. I added the line you provided. It solved one problem but created another. I restarted Apache and then I changed the name of my index.html file to index.php. I navigated to localhost and saw the same page I used to see when it was index.html So far, so good. But, when I clicked on the link to phpinfo.php I got the window that asks me what I want Firefox to do with the file, Open with [Browse...] or Save File. There were no entries in the error logs for Apache or for suPHP. I changed the file name back to index.html but get still have the same problem. So something else isn't right.

---

### Post by wojox on 2011-11-05
I'll look on my server at home after work tonight and tell you which file it is. I can't remeber right now.

---

### Post by moonguide on 2011-11-06
I have a vague memory of something like this happening a few years ago, and it wasn't Apache's fault -- at least I don't think it was.

I usually use Firefox, and that's where I experience the problem. I tried looking at the page with Midori and php still works. So Apache and suPHP are doing their thing.

I renamed index.html to index.php and found an error in /var/log/suPHP/suphp.log. It said index.php was writable by group. I changed the permission so that group is read only and now it works -- and that's with an empty httpd.conf.

Still doesn't work right with Firefox, though.

---

### Post by wojox on 2011-11-06
> **moonguide said:**
> 
Still doesn't work right with Firefox, though.

Empty the cache in Firefox.

---

### Post by moonguide on 2011-11-06
That was it. Thanks!

---

