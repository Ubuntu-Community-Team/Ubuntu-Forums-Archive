---
title: "trouble mouting webdav folder"
date: 2011-07-19
forum: General Help
---

### Post by mbeltoft on 2011-07-19
I'm trying to mount a webdav folder on my ubuntu 11.04 server with thiss command

```

sudo mount -t davfs https://vpzb24.docs.live.net/fd5b07486773d205/Billeder /home/beltoft/skydrive

```

but it's not working. I'm getting asked about username and password for the webdav folder but after I typed that in I get the error:

```

/sbin/mount.davfs: Mounting failed.
302 Found

```

It's not the credentials that it wrong as I can mount the webdav without problems on my Win7 machine

---

### Post by galvatron408 on 2011-07-25
yea, a 302 means you got redirected

are you sure that URI can be mounted via dav?

---

### Post by IIxpt on 2011-10-16
Any solution?
I have the same problem

bye!

---

### Post by _salem_ on 2011-12-16
I just had this problem crop up recently (December 2011) on my box.net account on ubuntu 11.10 64 bit. I don't know whether it was caused by a recent update to davfs or to box.net itself

I solved it by changing my fstab from [http://www.box.net](http://www.box.net) to [https://www.box.com](https://www.box.com)

then added a line in my secrets file for the updated url.

I'd read something about 302 being a redirect, so I swapped .net for .com in case the .net sever redirected to .com, and I added the S on httpS because I read something about making a secure connection....

it now works. yay!

---

### Post by Cicer on 2012-02-21
Thanks, _salem_!

---

### Post by IIxpt on 2012-02-21
I tried with skydrive, to do with .net i keep going the same but with .com:

```
 sudo mount -t davfs https://XXXXX.docs.live.com/XXXXXXXXXXXXXXXXX/Documentos /mnt/skydrive 
```And i get:

```
Please enter the username to authenticate with server
https://XXXX.docs.live.com/YYYYYYY/Documentos or hit enter for none.
  Username: mail@hotmail.com
Please enter the password to authenticate user maill@hotmail.com with server
https://xxxx.docs.live.com/YYYYYYYY/Documentos or hit enter for none.
  Password:  
/sbin/mount.davfs: connection timed out two times;
trying one last time
/sbin/mount.davfs: server temporarily unreachable;
mounting anyway
```Mount the folder but i can't see or create files: (

---

### Post by searchfgold6789 on 2012-09-05
Bump - i know that Gnome has libzapojit for accessing skydrive, but I'd really like to use Skydrive in Kubuntu. I get the same problem as llxpt...

---

