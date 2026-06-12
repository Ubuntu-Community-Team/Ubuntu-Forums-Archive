---
title: "owner of /var/www?"
date: 2012-02-09
forum: General Help
---

### Post by qwertyjjj on 2012-02-09
I just did this: sudo chown -R root:www-data /var/www

I still cannot access the oage: [http://localhost/catalog/install](http://localhost/catalog/install)
I get: Forbidden

You don't have permission to access /catalog/install on this server.
Apache/2.2.16 (Ubuntu) Server at localhost Port 80

Any ideas who the owner is supposed to be?

---

### Post by Noobeum on 2012-02-09
mb u need 

www-data.www-data ?

---

### Post by Lars Noodén on 2012-02-09
The owner is by default root:root so to set it back to the default,

```

sudo chown -R root:root /var/www

```

Having it owned by www-data is very unsafe, since that means the web server can write to the directory.


If you want to share write access to /var/www, one way would be the following:

```
 
sudo addgroup webmasters
sudo gpasswd --add qwertyjjj  webmasters

sudo chgrp -R webmasters /var/www
sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws  "{}" \;

```

That creates a group with you as a member and then gives write permissions to that group.

---

### Post by WorMzy on 2012-02-09
If you're getting a 401 or a 403, then the problem isn't the folder ownership; the problem probably lies with the .htaccess settings.

---

### Post by Habitual on 2012-02-09
> **wormzy said:**
> if you're getting a 401 or a 403, then the problem isn't the folder ownership; the problem probably lies with the .htaccess settings.

+1

---

### Post by qwertyjjj on 2012-02-09
> **WorMzy said:**
> If you're getting a 401 or a 403, then the problem isn't the folder ownership; the problem probably lies with the .htaccess settings.

I think 401 is htaccess, 403 is permissions.
I changed it to www-data:www-data and it worked.
The problem with root:root is that I can never edit the files using nautilus as it always prevents them from being loaded.

---

### Post by Lars Noodén on 2012-02-09
> **qwertyjjj said:**
> The problem with root:root is that I can never edit the files using nautilus as it always prevents them from being loaded.

That's why I recommended the recipe in #3 above.  It will allow you to edit the files.  Setting the owner to www-data:www-data gives write access by the web server, that's not necessarily a sound idea.  

If you need to grant read access to the web server, do it universally for everybody, so write access is not given:

```

sudo find /var/www -type d -exec chmod o=rx "{}" \;
sudo find /var/www -type f -exec chmod o=r  "{}" \;

```

---

### Post by qwertyjjj on 2012-02-15
ran step #3 above, seems to work.
Thanks

---

### Post by Lars Noodén on 2012-02-15
Something's gone wrong if the folders ended up being owned by www-data.  That's a situation you generally want to avoid because it gives write access to the web server.  The following will set them  back to system defaults:

```

sudo chown -R root:root /var/www

```

Then if you want you can repeat some of the steps in post #3

```

sudo chgrp -R webmasters /var/www
sudo find /var/www -type d -exec chmod g=rwxs,o=rx "{}" \;
sudo find /var/www -type f -exec chmod g=rws,o=r  "{}" \;

```

I don't know the details of OSCommerce.  Do any specific directories or files need write access?  If so, which user is the script being run as?

---

### Post by qwertyjjj on 2012-02-15
> **qwertyjjj said:**
> ran step #3 above, seems to work.
Thanks

only issue is that I will eventually need to upload all these development files to a webserver. On uploading, will the permissions remain like that of my development machine or will they be taken over by whatever the host has...usually webserver:webserver?

---

### Post by Lars Noodén on 2012-02-15
Any groups you've created locally won't exist on the remote server unless you also create them there too.  The question is whether it matters or not.  For you to publish web pages the only thing needed is that the webserver has read access to the files and directories.

---

### Post by qwertyjjj on 2012-02-16
> **Lars Noodén said:**
> Any groups you've created locally won't exist on the remote server unless you also create them there too.  The question is whether it matters or not.  For you to publish web pages the only thing needed is that the webserver has read access to the files and directories.

Well, in OSCommerce there are a number of sirectories that require write access for things like graphs, the images folder for uploaded images, etc. etc.
I think the permissions on those folders are set at a risky 777 but that is how OSCommerce does it. Will those permissions persist when copied by FTP, do the permissions persist or are they reconfigured when copied to different servers?

---

### Post by Lars Noodén on 2012-02-16
> **qwertyjjj said:**
> ... Will those permissions persist when copied by FTP, do the permissions persist or are they reconfigured when copied to different servers?

No.  Using FTP or SFTP, the files will get whatever the default settings are for your account on the destination machine.

---

