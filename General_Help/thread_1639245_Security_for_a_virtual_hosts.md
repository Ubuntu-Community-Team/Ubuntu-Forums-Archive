---
title: "Security for a virtual hosts"
date: 2010-12-06
forum: General Help
---

### Post by daj_uk on 2010-12-06
Hi there, sorry if this seems like a really baisc question.  I have been reading up on this over the last few days and my head is spinning!

I have successfully implemented virtual hosts on my server, my problem is security I think.

The virtual host has a folder and within that folder I want a user to be able to upload files to it.  The user can login via FTP and upload the files, but the permissions for each uploaded file always end up at 600, which means when visiting the site on a web browser the files are no accessible.  If I change the permissions to 644 I can access the file no problem on the browser.  However, I am still not sure that is the correct level.

how do I set the default the permissions for web access?  what is the correct permissions

I thought this entry for the site would do it...


<Directory /home/www/(mysitename)>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>


But I think I am mis-understanding something ](*,)

Any help much appreciated

---

