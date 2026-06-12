---
title: "Is there a list of Default File Permissions ?"
date: 2010-03-06
forum: General Help
---

### Post by iMisspell on 2010-03-06
Looking for a list of default file and dir permissions for *Ubuntu Server 8.04*

Was in ssh... fat fingered a sudo **chmod 0777 -R /***, so you can image the damage ive done. 

Spent time searching the net and have read its possible to restore the Default File Permissions, but have not read how, people where settling for just re-installing, which is something i do not want to do.

Humm... an idea that just popped into my head while typing this...

1) Installing Server 8.04 as a Virtual machine along with the programs im using, create a script to log the permissions of that install, then use that to restore to my current server ?

Anyone see a problem with that ?

2) Or use a live iso (never have looked at that before) ?


Any help would be great.


_

---

### Post by flippo on 2010-03-06
chmod shouldn't be recursive (without -R), so you should just have an issue in your root directory.

Here are the permissions in mine (I think they will be the same):
```
drwxr-xr-x   2 root root   4096 Mar  2 19:13 bin
drwxr-xr-x   4 root root   4096 Mar  1 16:19 boot
drwxr-xr-x  19 root root   4120 Mar  6 11:19 dev
drwxr-xr-x  80 root root   4096 Mar  6 13:46 etc
drwxr-xr-x   3 root root   4096 Aug 19  2009 home
drwxr-xr-x   8 root root   4096 Mar  1 01:19 lib
drwx------   2 root root  16384 Aug  3  2009 lost+found
drwxrwxr-x   3 root mount  4096 Mar  6 11:19 media
drwxr-xr-x  11 root root   4096 Aug 19  2009 mnt
drwxr-xr-x   9 root root   4096 Mar  1 13:16 opt
dr-xr-xr-x 165 root root      0 Mar  6 11:18 proc
drwx------  25 root root   4096 Mar  5 23:20 root
drwxr-xr-x   2 root root   4096 Mar  2 19:13 sbin
drwxr-xr-x  12 root root      0 Mar  6 11:18 sys
drwxrwxrwt  13 root root   4096 Mar  6 16:43 tmp
drwxr-xr-x  15 root root   4096 Aug 19  2009 usr
drwxr-xr-x  13 root root   4096 Aug 19  2009 var
```

---

### Post by iMisspell on 2010-03-06
Thanks for the start, flippo.

> **flippo said:**
> chmod shouldn't be recursive (without -R), so you should just have an issue in your root directory.
Recursive was used (typo in original post)... Just edited post to include that.

_

---

### Post by flippo on 2010-03-06
Ouch... thats pretty painful... Wish I had a good suggestion...

---

### Post by iMisspell on 2010-03-06
> **flippo said:**
> Ouch... thats pretty painful...
yup :(

In the mist of downloading the 8.04 iso now, gonna write a script to log permissions and see if that works.

Funny, ive been meaning to make a list of programs installed to make it eazyer down the line for fresh installs, that just worked its way to the top of the todo list :)

Will keep thread updated on process.

_

---

### Post by flippo on 2010-03-06
Yeah, I have a friend who runs arch, he has a script he keeps backed up: reinstall.sh

If he runs it, it will restore his entire PC back to its working order (without any personal files)

I personally keep my machine with an incremental backup on a server, but I don't think that would help if I ever had an issue like yours.

---

### Post by iMisspell on 2010-03-06
> **flippo said:**
> If he runs it, it will restore his entire PC back to its working order (without any personal files)
That will be added to the todo list.

The server is mainly for php and database's along with being a file server, all the php files and dbase's are on regular back-ups, which is how i ended up realizing there was a problem. MySQL whent to back up, errored out, sent off an email about it and here i am now. 

The lessons of paying attention can be a hard slap in the face.

_

---

### Post by iMisspell on 2010-03-07
After a few hours of playing around, the broken machine is now functioning again. I have not checked everything, but what i knew was broken before is now functioning correctly.

Wrote this up in case others want to try and restore there default file permissions with out having to re-install the o/s.
_[http://wiki.joescove.com/Restoring_Ubuntu_default_file_permissions](http://wiki.joescove.com/Restoring_Ubuntu_default_file_permissions)_

_

---

### Post by rnerwein on 2010-03-07
hi
no go !
you changed the permissions on the whole system - you will have fun
ciao

---

### Post by iMisspell on 2010-03-07
> **rnerwein said:**
> no go !
you changed the permissions on the whole system - you will have fun

Understood, that is why i did this...
_[http://wiki.joescove.com/Restoring_Ubuntu_default_file_permissions](http://wiki.joescove.com/Restoring_Ubuntu_default_file_permissions)_

_

---

