---
title: "PHP pages dont get executed...!!"
date: 2006-04-22
forum: General Help
---

### Post by und3rtug4 on 2006-04-22
Hi there!

I'm having this problem, that the apache2 server wont execute the .php files! It just displays the source code! 

I already have this server running pretty well and now, after a new installations, something is missing I guess!

I took the same steps as on the previous installation, but i kind find the solution for this problem!

The proper permissions and such were given to the files (even 777) and it stills the same!

Regards...

---

### Post by jazzmuzik on 2006-04-22
Did you install libapache2-mod-php5  via Synaptic?

---

### Post by MJN on 2006-04-22
And have you searched/trawled the forum? This query is starting to become FAQ #1  ...

Mathew

---

### Post by und3rtug4 on 2006-04-22
I'm using php4! And yes, the mod is installed!
Everything seems to be installed and running, but it just wont execute them!
Its displays the following signature: 
 Apache/2.0.54 (Ubuntu) PHP/4.4.0-3ubuntu2 mod_ssl/2.0.54 OpenSSL/0.9.7g

... so it seems to have the php mod installed and loaded!

First time that this appens, so i dont get it! What could be the problem!?

Thanks!

---

### Post by jazzmuzik on 2006-04-22
Didn't you ask this question before? Maybe it was somebody else. There may be a solution already posted here.

I don't have version 4 installed, so I'm guessing, but do you have an AddType for the php mod in apache.conf (or is it httpd.conf)?

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

Or something simlar. Really though, search around.

This thread [http://ubuntuforums.org/showthread.php?t=156472&highlight=addtype+php](http://ubuntuforums.org/showthread.php?t=156472&highlight=addtype+php) mentions the need to clear your browser cache. You might also try a Shift-Reload (Hold down shift key and click the Reload button in Firefox).

---

### Post by und3rtug4 on 2006-04-22
Yes, I already crawled the forum in the quest for the answer!
All always try to make the things by myself, I make the question because i really didnt know what the problem was!

Anyway, I already found the bottleneck of the problem and its already working 100%!

Thanks anyway!

und3rtug4

---

### Post by und3rtug4 on 2006-04-22
[QUOTE=jazzmuzik]Didn't you ask this question before? Maybe it was somebody else. There may be a solution already posted here.

I don't have version 4 installed, so I'm guessing, but do you have an AddType for the php mod in apache.conf (or is it httpd.conf)?

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

Or something simlar. Really though, search around.

This thread [http://ubuntuforums.org/showthread.php?t=156472&highlight=addtype+php](http://ubuntuforums.org/showthread.php?t=156472&highlight=addtype+php) mentions the need to clear your browser cache. You might also try a Shift-Reload (Hold down shift key and click the Reload button in Firefox).[/QUOTE]


Yes the problem was on /etc/apache2/mods-enabled/php4.conf !!!
I just uncomment the :

<IfModule mod_php4.c>
#  AddType application/x-httpd-php .php .phtml .php3
#  AddType application/x-httpd-php-source .phps
</IfModule>

and now its working!

Thanks for the help!

---

### Post by jazzmuzik on 2006-04-22
Yea! I was sort of close. hehe

---

### Post by LordMerlin on 2006-04-25
<IfModule mod_php4.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

This is what my /etc/apache2/mods-enabled/php4.conf looks like, yet when I try and run a .php file, firefox wants to save it to the HDD. 

```

root@Gimbli:/home/samba/software/source/xfprot-1.15# a2enmod php4
This module is already enabled!

```

What am I missing?

---

