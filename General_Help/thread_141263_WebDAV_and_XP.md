---
title: "WebDAV and XP?"
date: 2006-03-07
forum: General Help
---

### Post by acegolfer on 2006-03-07
I'm trying to access WebDAV folder from XP but failed. XP asks the id and password over and over. 

I tried 3 things but all failed.

1. add # such as [http://192.168.1.7/davhome/#](http://192.168.1.7/davhome/#)
2. add port number [http://192.168.1.7:80/davhome](http://192.168.1.7:80/davhome)
3. using id with @ such as [email]name@server.org[/email] to trick XP not to add the computer name

BTW, samba is working within the home network but I'd like to access the folder from my office. In addition, I can see the folder in IE but can't add the network place.

Here's my httpd.conf file.

```
# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so
DAVLockDB /var/lock/apache2/DAVLock
#DAVMinTimeout 600
BrowserMatch "^WebDAVFS/1.[012]" redirect-carefully
BrowserMatch "Microsoft Data Access Internet Publishing Provider" redirect-carefully
BrowserMatch "Microsoft-WebDAV-MiniRedir/5.1.2600" redirect-carefully
BrowserMatch "^WebDrive" redirect-carefully
BrowserMatch "^WebDAVFS" redirect-carefully


<ifmodule mod_headers.c>
Header add MS-Author-Via "DAV"
</ifmodule>

<ifmodule mod_encoding.c>
EncodingEngine on
NormalizeUsername on
</ifmodule>


Alias /dav /tmp/dav

<Location /davhome/>
        Dav On

        AuthType Digest
        AuthName ace@server.com
        AuthUserFile /var/www/davhome/.DAVlogin

</Location>

```

---

### Post by acegolfer on 2006-03-11
I finally got it to work after searching hundreds of links. I changed location to directory and specify the full path in my httpd.conf file.

I can now read write my files from my office and can read from anywhere.

```
<Directory /var/www/davhome>
        Dav On
        AuthType Basic
        AuthName "userid"
        AuthUserFile /"yourpathto"/.htpasswd

</Directory>
```

---

### Post by anglerud on 2006-08-25
Thank you very much for this post, it's been very helpful! 

As I was only enabling dav for a vhost, I was adding all my config changes to the vhost's config in sites-enabled/<my vhost config file>. Turns out, XP wasn't completely happy mounting a directory until I'd made sure both the BrowerMatch and ifmodule blocks were in the main apache2.conf file. (konqueror, cadaver and others however worked fine)

So, if anyone else is having trouble getting XP to mount the dir properly as a web folder, give that a shot, see if it helps. 


I came across a lot of misinformation while googling up solutions to this, several of the more devious ones claimed XP SP2 required Digest authentication - this is **wrong** - it works fine with Basic Auth (as the fine post above clearly shows).

---

### Post by woodmanf on 2008-01-02
I can get Win XP to see the folders and files but Windows can't open in place. For example, open an MP3 in place with Media Player does nothing. Right Click Open is not available. Other file manipulation funtions work (rename, copy ...)

Any ideas?

---

