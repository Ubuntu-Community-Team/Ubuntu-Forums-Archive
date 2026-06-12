---
title: "Disable caching in Apache2"
date: 2009-09-21
forum: General Help
---

### Post by Ralf.G on 2009-09-21
Hi,
I having difficulties disabling the automatic caching using the Ubuntu Apache installation.
I am serving dynamic .m3u playlist files which are updated every couple of seconds, but the server keeps serving an old version of the file.

I am running Ubuntu 8.10 with the standard Apache 2.2.9

So far I've tried 
1) using the .htaccess file with the following lines:
<FilesMatch "\.(m3u|m3u8|ts)$">
Header set Cache-Control "max-age=0, private, must-revalidate"
</FilesMatch>
I did restart the server and made sure the the headers module is loaded but that didn't help. The htaccess access control is working but still the old file is served.

2) I've tried adding the following to httpd.conf
<IfModule mod_cache.c>
CacheDisable "/var/www/HttpShare"
</IfModule>
, where /var/www/HttpShare and it's subfolders contain the playlist files.
Again I made sure that mod_cache.c had been added and restarted the server.

Does anyone know what I'm doing wrong?

Thanks,
Ralf

---

### Post by Ralf.G on 2009-09-24
Anyone please?

The weird thing is also that the directory listing does update the last modified times of the playlist, yet the content must be being cached somewhere in memory since it serves the old file.

---

### Post by wojox on 2009-09-24
Try this:

```
sudo a2enmod headers
```

Throw this into a .htaccess

```
Header set Expires "Thu, 19 Nov 1981 08:52:00 GM"
Header set Cache-Control "no-store, no-cache, must-revalidate, post-check=0, pre-check=0"
Header set Pragma "no-cache"

```

---

### Post by Ralf.G on 2009-09-24
Hi, thanks for the reply.

The headers module was already enabled, and I added the suggestion to the .htaccess but unfortunately no change.

The weird thing is after modifying the playlist file to be downloaded on the server, the modifed time and the change in size are reflected in the index. But after downloading the file it's always still the old content. And if there has been a change in file size, there's a bunch of junk characters following the original data.

PS: Just discovered something new: if I repeat my steps with a standard .txt file, I receive the updated content each time. Seems it's the .m3u extension that is causing the trouble.
Any ideas where besides in the .htaccess file I need to configure apache to reload .m3u files from disk? (Since the <FilesMatch "\.(m3u|m3u8|ts)$"> statement didn't do the trick)

Thanks!

---

### Post by Ralf.G on 2009-09-24
FYI: adding
EnableSendfile Off 
to the configuration solved the problem.

---

### Post by wojox on 2009-09-24
Sweet

---

### Post by choclatboy on 2009-11-07
thanks,

it worked for me.

---

### Post by adfasdfadsfadsf on 2012-12-17
I've been searching Google for 15 minutes for a solution on how to prevent server caching.  Adding "EnableSendfile Off" to my httpd.conf and restarting Apache (sudo ./apachectl -k restart) did the trick.  Thanks for posting the solution.

EDIT: Nevermind it didn't work.  I think just restarting the server worked.  Still searching for a solution.

---

