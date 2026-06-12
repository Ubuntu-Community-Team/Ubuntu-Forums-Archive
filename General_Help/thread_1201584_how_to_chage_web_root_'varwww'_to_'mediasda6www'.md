---
title: "how to chage web root '/var/www/' to '/media/sda6/www'"
date: 2009-07-01
forum: General Help
---

### Post by gaurishpatil on 2009-07-01
hi..
I want change my '/var/www/' path to '/media/sda6/www/'..
I tried to change in '/etc/apache2/sites-available/default' file as below

**originally..**

DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
**After Change...**
DocumentRoot /media/sda6/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /media/sda6/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

but.. when I try to access my file I got error..
as ...
'access denied'

I tried to change the permission of file on my sda6 but doesn't changes at all(even I logged as a root in ubuntu)..
can any budy help..
thanks in advance...

---

### Post by John Cheng on 2009-07-01
Sounds like you are able to change your web root (DocumentRoot).

If you can't change the permissions on that drive, the problem may be the way you mounted /metida/sda6/www, or heck, it might be a USB drive with some sort of "write-protect switch".

I am wondering if you mounted that device read only. What does your /etc/fstab look like?

---

