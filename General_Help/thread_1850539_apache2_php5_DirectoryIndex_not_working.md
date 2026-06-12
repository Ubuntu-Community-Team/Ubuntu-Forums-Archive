---
title: "apache2 php5 DirectoryIndex not working"
date: 2011-09-26
forum: General Help
---

### Post by btodd01 on 2011-09-26
Hi - Help!!
I am running 

 Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.9 with Suhosin-Patch configured.

I have converted my pages from html to php and I can't get index.php (and or) index.html to load.

I have this in httpd.conf
<Directory /var/www/>
   DirectoryIndex index.php index.html
   AddType text/html .php
</Directory>

with that - index.php loads but if I make it unreadable,
index.html does not work.
I get -  PHP Fatal error:  Unknown: Failed opening required '/var/www/kofc/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

If I reverse the statement..
DirectoryIndex index.html index.php
then index.html loads and if it is not readable, index.php
is not looked at.

I do have dir.conf in mods-enabled and it contains...

<IfModule mod_dir.c>
   DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm

It seems like the DirectoryIndex statement only is looking
at the first option. Or is something else screwed up?
My php pages work just fine if I specify the file name

Eg. [http://....../.../index.php](http://....../.../index.php)

Linux todd-GX270 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux
todd@todd-GX270:/etc/apache2$ cat /etc/issue
Ubuntu 10.04.3 LTS \n \l

I'm stuck!
Thanks
Bob

---

### Post by Doug S on 2011-09-26
As far I can tell from your description, everything is working properly, but maybe I didn't understand something. You will only get a directory listing if all of the other files are not there. In my case, that is exactly how I want it. For the index.html index.php order swapping stuff, it doesn't matter about reabable or not, only if they are there or not. Of course, the readability part gives either an error or no error. You can verify what I have said by experiment: Remove any index.??? file from a directory and verify that you get a directory listing if you enter a URL pointing to that directory; When your order is index.php index.html remove the index.php and verify that index.html is used if you enter a URL pointing to that directory. (Note: I did not actually do this experiment myself, but I might later, if I have time.)

---

### Post by btodd01 on 2011-09-27
Hi - maybe I did not explain properly.

In the directory, I want either index.html or index.php to load if they 
exist. If they don't - I expect nothing to load.

What is happening though, is that with the config I showed...
index.php loads if it exists (if I make index.php not readable or
executable the behavior is the same as if the file doesn't exit).
In that case, index.html should load if it is there. But it doesn't.
Apache complains that it can't find index.php.

If I reverse the order
DirectoryIndex index.html index.php
Then index.html loads.
If I remove index.html from the directory and index.php is there...
I get an error that index.html is not found!!! instead of index.php loading.

I hope that is clearer.
Bob

---

### Post by Doug S on 2011-09-27
I did the experiment I suggested in my first reply, and it worked just like I had stated. I also did the make it not readable stuff and that worked just like I had stated, i.e. on my system, it did not go onto the next file but rather complained about the first file being not readable.
On my system httpd.conf is empty, and the dir.conf file is used for this stuff. I also don't have the AddType line anywhere that I could find. However, I notice that our systems differ for versions of Ubuntu and Apache and PHP. Sorry, I have not been any help.

---

### Post by btodd01 on 2011-09-27
Doug
Thank you for trying. I cleanup my httpd.conf. Nothing there should have affected what I was doing - but - magically, it started working how I expected it to do.

Thanks again,
I will close this off and if I figure out what got me I will post it.

Bob

---

