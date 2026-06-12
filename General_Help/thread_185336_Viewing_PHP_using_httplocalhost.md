---
title: "Viewing PHP using http://localhost"
date: 2006-05-31
forum: General Help
---

### Post by ChrisNTR on 2006-05-31
I installed mySql + Apache and PHP fine. Was able to view php pages etc. But not when I try and view a php file, it tries to open it with gedit and won't open up in the browser (firefox). Can anyone help?

---

### Post by MadMan2k on 2006-05-31
its intended to work that way.

---

### Post by ChrisNTR on 2006-05-31
[QUOTE=MadMan2k]its intended to work that way.[/QUOTE]

It's meant to work like this : 
[[img=http://img413.imageshack.us/img413/2605/screenshot252dw.th.png]](http://img413.imageshack.us/my.php?image=screenshot252dw.png)

Before it opened up in the browser which is what I want :(

---

### Post by ssam on 2006-05-31
have you put it in /var/www ?

---

### Post by arizonagroovejet on 2006-05-31
I think you need to add the php module to your apache modules.conf file then restart apache.

I'm using apache 1.3 and php 4 (because that's what my hosting company uses)  add I had to add this line to the end of /etc/apache/modules.conf

LoadModule php4_module /usr/lib/apache/1.3/libphp4.so

Then restart apache with 

sudo /etc/init.d/apache restart

libphp4.so is part of the libapache-mod-php4 package.

hth,

mike

---

### Post by nashjc on 2006-07-27
Thanks for the post about apache1.3 and php4. I was having same trouble.

Now I'm working fine for php, but on installing phpmyadmin, if I use
[http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)  it offers to download something. However, if I
add index.php at the end, things work. I've looked at httpd.conf, thinking it was some sort of setting there. I uncommented the lines
   AddType application/x-httpd-php .php
    AddType application/x-httpd-php-source .phps

there in order to get stuff going. 

Seems like the symbolic link of phpmyadmin in /var/www is somehow not quite right (points to /usr/share/phpmyadmin.

Any ideas. 

JN

---

### Post by jimmygoon on 2006-07-28
"sudo aptitude install php5 apache2 mysql-server mysql-client"

With that command it should have automagically found out that you were installing all of AMP and it should have installed the stuff to link them all together.

I type that one command and I've NEVER EVER had to edit any config files... :D

---

### Post by NewbieNik on 2006-07-28
> **jimmygoon said:**
> "sudo aptitude install php5 apache2 mysql-server mysql-client"

With that command it should have automagically found out that you were installing all of AMP and it should have installed the stuff to link them all together.


Which is fine if you want to use apche2 and PHP5, but there are PHP modules that don't work with 5, only 4.

---

### Post by jimmygoon on 2006-07-28
> **NewbieNik said:**
> Which is fine if you want to use apche2 and PHP5, but there are PHP modules that don't work with 5, only 4.
the same thing works for 4 .. just swap it to php4 instead of php5... it still inserts the connecting packages...

... what still has to use php4 anyways  :!::-&

---

### Post by nashjc on 2006-07-28
I know folk like the automagic, BUT (and it's bigger than mt everest), sometimes the people doing the setup just cannot tie up all the loose ends, and there are quite a few of them in Ubuntu still (and in Windoze etc.) Too many cooks.

Anyway, after using the suggestion above to put in apache2 php5 etc., things did not work any differently. In fact, apache2 was not started, and even when apache stopped, the System/Administration/Services seemed to work but didn't actually start it. Manual try
 /etc/init.d/apache2 start
chown: changing ownership of `/var/lock/apache2': Operation not permitted
john@JNTWRU:~$ sudo /etc/init.d/apache2 start
 * Starting apache 2.0 web server... apache2: could not open document config file /etc/apache2/apache2.conf

I think I need more than automagic. And I'd actually prefer apache1.3 and php4 to match the production server that things will be going onto later.

I'll try to report back when I find why things are not linking. I suspect its something like the umask issue I reported for samba and which also seems to apply to floppy mount (another problem I'm trying to resolve so some scripts to back up key config files to floppy in a single click can be made to work and do the mount and unmount reliably). Still lots to do to get things simple.

JN

---

### Post by nashjc on 2006-07-28
Just making sure apache and php4 (not apache2 and php5) were active seemed to get things running. Removal of extra stuff seems to be very important.

This won't necessarily resolve the issue for those wanting apache2 and php5.

JN

---

### Post by jimmygoon on 2006-07-28
> [SIZE=1]Backup /var/www and any other place that is serving web pages.

"sudo aptitude purge apache apache2 php php5 php4 mysql mysql-common mysql-server mysql-client"
[B]
to use php4:[/B] "sudo aptitude install apache2 php4 mysql-client mysql-server mysql-common"
**to use php5:** "sudo aptitude install apache2 php5 mysql-client mysql-server mysql-common"

And that doesn't work?[/SIZE][SIZE=1]


[SIZE=2]After reading through the thread again, I decided that the above that *had *posted probably still won't help...[/SIZE]
[/SIZE]

---

