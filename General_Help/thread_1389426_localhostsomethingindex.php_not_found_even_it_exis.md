---
title: "/localhost/something/index.php not found even it exists"
date: 2010-01-24
forum: General Help
---

### Post by nikolayivanovbg on 2010-01-24
I have a very strange problem.
Few days ago everything was working fine.
Now every site I'm developing under /var/www doesn't open at all.
If i have a file /var/www/siteone/index.php, when i try to open [http://localhost/siteone/index.php](http://localhost/siteone/index.php) it's not opening. And IT USED TO OPEN few days ago.
It seems that php is working: [http://localhost/index.php](http://localhost/index.php) is working.
I'm using .htaccess in subfolders. I remove it for tests - nothing changed.

What new i did to my Ubuntu:
Installing of VMware Server 2.0.2 + Windows XP as a guest. Works fine.

Strange error/warning from error.log in apache2 folder:

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/apc.so' - /usr/lib/php5/20060613+lfs/apc.so: cannot open shared object file: No such file or directory in Unknown on line 0

[Sun Jan 24 18:34:02 2010] [error] [client 127.0.0.1] File does not exist: /var/www/siteone/localhost

Why this **localhost** appears at the end of line?

I'm using linux/ubuntu for about 3 months already - i'm not confident with it.

Any help is appreciated!
Thanks

---

### Post by Lekensteyn on 2010-01-24
How did you install your server?
Any .htaccess / php ini settings that may affect this?

---

### Post by nikolayivanovbg on 2010-01-25
.htaccess was deactivated(renamed). Nothing has changed after that.

From here i get a script and info how to install VMware 2.0.2:
[http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/](http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/)

If you are asking for installing Apache2 + PHP + MySQL ... i'm not sure :(
I used to use windows from more than 15 years - developing applications using Visual Studio (6.0 and .NET) from Microsoft. So, i'm very new to linux.

From year i'm focused on PHP/MySQL and i become sick of Windows ...
I decided 2-3 months ago to switch to linux.
Installing Ubuntu with everything needed took me 2 days of hard reading, testing installing and uninstalling different things. One more day to choose which editor to use. That's why i cannot say how i used to install Apache, PHP and so on.

I'm even considering to install kubuntu instead of ubuntu. One friend of mine told me that KDE is better.

---

