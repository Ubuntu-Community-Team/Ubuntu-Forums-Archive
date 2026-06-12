---
title: "Apache2 Options Indexes does not work"
date: 2010-03-27
forum: General Help
---

### Post by wwuster on 2010-03-27
I'm running 9.10 and apache2.

I have a virtual host: [http://www.hindbrain.net](http://www.hindbrain.net)
This works. I'm trying to share some files in a directory:
[http://www.hindbrain.net/test](http://www.hindbrain.net/test)

I added this in the virtualhost section:

<Directory "/var/www/hindbrain/test">
   Options Indexes MultiViews +FollowSymLinks
   IndexOptions +FancyIndexing
   AllowOverride All
   order allow,deny
   allow from all
</Directory>

I added 2 test files in this directory: test1.txt and test2.txt. If you go
to this test page you don't see any files, just a directory listing header. I set the ownership of the directory and files to www-data, and
the permission of the files to 644, and the test directory to 755, and I did restart apache2.

Why don't the files show up?

thanks,
William

---

### Post by gmargo on 2010-03-27
Try (note the plus signs):
```

Options +Indexes +MultiViews +FollowSymLinks

```

---

### Post by spiderbatdad on 2010-03-27
Yes or make sure none of the options have + or - signs.
A little research into configuring options, I think will reveal that apache2
tends to misbehave when options are given with symbols, especially if some options have symbols and some do not. Either list the option, or leave it out...is my understanding.
```
<Directory "/var/www/hindbrain/test">
Options Indexes MultiViews FollowSymLinks
IndexOptions FancyIndexing
AllowOverride All
order allow,deny
allow from all
</Directory>
```

Also try loosing the IndexOptions FancyIndexing.
Consult your logs.

---

### Post by wwuster on 2010-03-27
I added +'s to all of the options, got rid of fancyindexing, and checked the apache error and access logs. It still doesn't work and there is no error in the error.log file.

William

---

### Post by gmargo on 2010-03-27
The link you gave, [http://www.hindbrain.net/test/](http://www.hindbrain.net/test/), is showing an index now, but with no files in it.

---

### Post by wwuster on 2010-03-27
> **gmargo said:**
> The link you gave, [http://www.hindbrain.net/test/](http://www.hindbrain.net/test/), is showing an index now, but with no files in it.

Yes. That's been the problem. There are 2 files in the directory: test1.txt and test2.txt. I can't get them to show up.

-rw-r--r-- 1 www-data www-data 7 2010-03-27 05:48 test1.txt
-rw-r--r-- 1 www-data www-data 7 2010-03-27 05:48 test2.txt

William

---

### Post by new_tolinux on 2010-03-27
When I look in my virtual site-file I'm missing the DocumentRoot entry in your file.
Mine looks like this:
```
*edited out*
DocumentRoot /my/www/root
    <Directory /my/www/root>
*edited out*
```

And it works like a charm.

---

### Post by spiderbatdad on 2010-03-27
I think the problem is that your directory permission is wrong. Directories need +x in order to be searchable...755 for example.
I noticed this link works:
[http://www.hindbrain.net/test/test1.txt](http://www.hindbrain.net/test/test1.txt)

---

### Post by wwuster on 2010-03-28
> **spiderbatdad said:**
> I think the problem is that your directory permission is wrong. Directories need +x in order to be searchable...755 for example.
I noticed this link works:
[http://www.hindbrain.net/test/test1.txt](http://www.hindbrain.net/test/test1.txt)

the test directory is 755:

drwxr-xr-x  2 www-data www-data     4096 2010-03-27 05:48 test/

it has 2 .txt files set to 644 as described earlier. Apache2 refuses to show them.

William

---

### Post by gmargo on 2010-03-28
Here's a test I tried on Karmic.  With a stock apache install (aptitude -V -R install apache2-mpm-prefork), the system documentation directory is set up to display with an index.  So "http://localhost/doc/" shows the directory listing of /usr/share/doc/.  Does this work for you?

---

### Post by wwuster on 2010-03-29
> **gmargo said:**
> Here's a test I tried on Karmic.  With a stock apache install (aptitude -V -R install apache2-mpm-prefork), the system documentation directory is set up to display with an index.  So "http://localhost/doc/" shows the directory listing of /usr/share/doc/.  Does this work for you?

On the same machine [http://localhost/doc/](http://localhost/doc/) works. Maybe something is wrong with my virtualhost section. Here it is:

<VirtualHost *>
   ServerAdmin [email]webmaster *at* hindbrain.net[/email]
   ServerName  [www.hindbrain.net](www.hindbrain.net)
   ServerAlias hindbrain.net
   AddHandler cgi-script .rb
   AddType application/x-httpd-eruby .rhtml

   DirectoryIndex index.php

   DocumentRoot /var/www/hindbrain
   ScriptAlias /cgi-bin/ /var/www/hindbrain/

   <Location />
      Options +ExecCGI
   </Location>


   <Directory "/var/www/hindbrain/test">
      Options +Indexes +MultiViews +FollowSymLinks
      AllowOverride All
      order allow,deny
      allow from all
   </Directory>

   ErrorLog  /var/www/hindbrain/logs/error.log
   CustomLog /var/www/hindbrain/logs/access.log combined

</VirtualHost>

/etc/apache2/apache2.conf is not modified by me, and httpd.conf is empty.

Do I need to change anything in the virtualhost section?

William

---

### Post by spiderbatdad on 2010-03-29
I think your use of ServerAlias is not in keeping with Apache2's documentation. Please correct me if I'm wrong.
[http://httpd.apache.org/docs/1.3/vhosts/name-based.html](http://httpd.apache.org/docs/1.3/vhosts/name-based.html)

bleh. I keep forgetting the page shows...just isn't indexing sorry.

Have you tried getting rid of all those +'s

---

### Post by wwuster on 2010-03-29
Yes, I just tried that. No change. Some setting somewhere is preventing the directory listing.

The only other .conf file that I'm aware of that might have something to do with this is autoindex.conf. So, here it is (with the comments removed to save space). This is the stock file and refers to /icons/ but there is no such directory, in case that matters.

<IfModule mod_autoindex.c>
IndexOptions FancyIndexing VersionSort HTMLTable NameWidth=* DescriptionWidth=* Charset=UTF-8

AddIconByEncoding (CMP,/icons/compressed.gif) x-compress x-gzip x-bzip2

AddIconByType (TXT,/icons/text.gif) text/*
AddIconByType (IMG,/icons/image2.gif) image/*
AddIconByType (SND,/icons/sound2.gif) audio/*
AddIconByType (VID,/icons/movie.gif) video/*

AddIcon /icons/binary.gif .bin .exe
AddIcon /icons/binhex.gif .hqx
AddIcon /icons/tar.gif .tar
AddIcon /icons/world2.gif .wrl .wrl.gz .vrml .vrm .iv
AddIcon /icons/compressed.gif .Z .z .tgz .gz .zip
AddIcon /icons/a.gif .ps .ai .eps
AddIcon /icons/layout.gif .html .shtml .htm .pdf
AddIcon /icons/text.gif .txt
AddIcon /icons/c.gif .c
AddIcon /icons/p.gif .pl .py
AddIcon /icons/f.gif .for
AddIcon /icons/dvi.gif .dvi
AddIcon /icons/uuencoded.gif .uu
AddIcon /icons/script.gif .conf .sh .shar .csh .ksh .tcl
AddIcon /icons/tex.gif .tex
AddIcon /icons/bomb.gif core
AddIcon (SND,/icons/sound2.gif) .ogg
AddIcon (VID,/icons/movie.gif) .ogm

AddIcon /icons/back.gif ..
AddIcon /icons/hand.right.gif README
AddIcon /icons/folder.gif ^^DIRECTORY^^
AddIcon /icons/blank.gif ^^BLANKICON^^

# Default icons for OpenDocument format
AddIcon /icons/odf6odt-20x22.png .odt
AddIcon /icons/odf6ods-20x22.png .ods
AddIcon /icons/odf6odp-20x22.png .odp
AddIcon /icons/odf6odg-20x22.png .odg
AddIcon /icons/odf6odc-20x22.png .odc
AddIcon /icons/odf6odf-20x22.png .odf
AddIcon /icons/odf6odb-20x22.png .odb
AddIcon /icons/odf6odi-20x22.png .odi
AddIcon /icons/odf6odm-20x22.png .odm

AddIcon /icons/odf6ott-20x22.png .ott
AddIcon /icons/odf6ots-20x22.png .ots
AddIcon /icons/odf6otp-20x22.png .otp
AddIcon /icons/odf6otg-20x22.png .otg
AddIcon /icons/odf6otc-20x22.png .otc
AddIcon /icons/odf6otf-20x22.png .otf
AddIcon /icons/odf6oti-20x22.png .oti
AddIcon /icons/odf6oth-20x22.png .oth

DefaultIcon /icons/unknown.gif

ReadmeName README.html
HeaderName HEADER.html

</IfModule>

---

### Post by gmargo on 2010-03-29
Here is a virtual host file that works for me.  It's a modified version of yours, but at the moment without any cgi, ruby, or php stuff.  Just the basics.  Give it a try.  It should give us a building block.

```

NameVirtualHost *:80
<VirtualHost _default_:80>

ServerName www.hindbrain.net
ServerAdmin "webmaster *at* hindbrain.net"
ServerAlias hindbrain.net

DocumentRoot /var/www/hindbrain

<Directory />
        Order Deny,Allow
        Deny from all
</Directory>

<Directory "/var/www/hindbrain">
        Options FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
</Directory>

<Directory "/var/www/hindbrain/test">
        Options Indexes MultiViews FollowSymLinks
        IndexOptions +NameWidth=*
        AllowOverride None
        Order deny,allow
        Allow from all
</Directory>

ErrorLog  /var/www/hindbrain/logs/error.log
CustomLog /var/www/hindbrain/logs/access.log combined

# Possible values: debug, info, notice, warn, error, crit, alert, emerg.
LogLevel warn

ServerSignature On

</VirtualHost>



```

---

### Post by wwuster on 2010-03-29
gmargo,
   I put your virtualhost section into the sites-available file and restarted apache2. No change... Also, no errors in the log file, other than outsiders trying to access error.log ;)


William

---

### Post by gmargo on 2010-03-29
> **wwuster said:**
> Also, no errors in the log file, other than outsiders trying to access error.log ;)

That was me. :p

---

### Post by gmargo on 2010-03-29
Something is really amiss.  I used the exact same options as the /usr/share/doc directory, which you said worked for you.  (Not quite exact - added IndexOptions and Allow from all.) How can that be?

The files in your test directory - they are local or symbolic links?

Are you fully stopping/starting apache?

---

### Post by wwuster on 2010-03-29
> **gmargo said:**
> Something is really amiss.  I used the exact same options as the /usr/share/doc directory, which you said worked for you.  (Not quite exact - added IndexOptions and Allow from all.) How can that be?

The files in your test directory - they are local or symbolic links?

Are you fully stopping/starting apache?


The files in the test directory are local:
-rw-r--r-- 1 www-data www-data   7 2010-03-27 05:48 test1.txt
-rw-r--r-- 1 www-data www-data   7 2010-03-27 05:48 test2.txt

the test directory:
drwxr-xr-x  2 www-data www-data     4096 2010-03-29 13:33 test/


I restart apache2 with /etc/init.d/apache2 restart

Something IS amiss.

William

---

### Post by Bashi88 on 2010-06-17
I wrestled with this exactly same problem whole night.. Suddenly i got everything working again.

This is my apache2.conf addition:

```
<Directory />  
Order Deny,Allow
Deny from all
</Directory>
<Directory /var/www>
Order Deny,Allow
Allow from all
</Directory>
<Directory /var/www/share>
Options Indexes
</Directory>

```

And this is /etc/apache2/sites-available/default:

```
DocumentRoot /var/www
       
 <Directory />
Options -FollowSymLinks
 AllowOverride None
 </Directory>
 <Directory /var/www/>
Options None
AllowOverride None
Order allow,deny
allow from all
 </Directory>

```

"share" is the directory which contents are indexed and public. When i put more directives for "share" the indexing stops working for some reason, that's where i stumbled for a long time. I also removed everything considering that "share"-directory from the virtual host configuration file. "mod_autoindex" is enabled.

I didn't have any specific error messages in the log, just informing that "Attempt to serve directory xxxxxxx".

Files and directories all have 750 permissions where owner is my username and group is "apache" (i have apache run as its own user).

This is the final solution which happens to work, hopefully this is helpful for someone. Had to register because of this :lolflag:

---

