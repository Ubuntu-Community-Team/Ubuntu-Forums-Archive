---
title: "Package manager failure"
date: 2009-08-11
forum: General Help
---

### Post by rogerw05465 on 2009-08-11
New to the Forum, so apologies if I screw up the protocols. Layer 8 is always the hardest...

In adding a printer driver the dpkg failed, the message saying it needed to be re-installed. But it won't install withouth the error. Now any package manager effort gives problems: Synaptic gives a similar error and won't run: 

"E: the package mfc6800lpr needs to be reinstalled, but I can't find and archive for it.
E: Internal error opening cache (1). Please report"

The command dpkg -l |grep mfc shows both the CUPSwrapper and the mfc6800lpr, but I cannot remove the mfc6800lpr. There is an error that says it is is "in a very bad inconsistant state - you shoudl reinstall before removing"

Can't go forward, can't go back..

Thanks for any enlightenment.

Roger

---

### Post by wojox on 2009-08-11
Open the terminal:

```
sudo apt-get --reinstall install mfc6800lpr
```

See if that helps.

---

### Post by rogerw05465 on 2009-08-11
> **wojox said:**
> Open the terminal:

```
sudo apt-get --reinstall install mfc6800lpr
```

See if that helps.
Wojox, thanks for the quick reply!

No luck. It tried, but: 
rogerw@rogerw-acer:~$ sudo apt-get --reinstall install mfc6800lpr
[sudo] password for rogerw: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc6800lpr needs to be reinstalled, but I can't find an archive for it.
rogerw@rogerw-acer:~$

---

### Post by wojox on 2009-08-11
Ok:

```
dpkg --remove --force-remove-reinstreq mfc6800lpr
```

---

### Post by rogerw05465 on 2009-08-11
> **wojox said:**
> Ok:

```
dpkg --remove --force-remove-reinstreq mfc6800lpr
```
Wojox, this is like pulling nails out of old oak....

No luck:
rogerw@rogerw-acer:~$ sudo dpkg --remove --force-remove-reinstreq mfc6800lpr
[sudo] password for rogerw: 
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 104427 files and directories currently installed.)
Removing mfc6800lpr ...
/var/lib/dpkg/info/mfc6800lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing mfc6800lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc6800lpr
rogerw@rogerw-acer:

I also tried this:
rogerw@rogerw-acer:~$ sudo aptitude -f remove mfc6800lpr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  libpq5{u} menu{u} mfc6800lpr 
0 packages upgraded, 0 newly installed, 3 to remove and 182 not upgraded.
Need to get 0B of archives. After unpacking 2896kB will be freed.
Do you want to continue? [Y/n/?] 

As it seemed to require the removal of a library, I thought I would ask if I should proceed. Thoughts?

Roger

---

### Post by wojox on 2009-08-11
libpq is a C library that enables user programs to communicate with the PostgreSQL database server. The server can be on another machine and accessed through TCP/IP. This version of libpq is compatible with servers from PostgreSQL 8.2 or later. Do you have this DB installed.

---

### Post by rogerw05465 on 2009-08-11
> **wojox said:**
> libpq is a C library that enables user programs to communicate with the PostgreSQL database server. The server can be on another machine and accessed through TCP/IP. This version of libpq is compatible with servers from PostgreSQL 8.2 or later. Do you have this DB installed.
Not sure how to know what libraries are installed, but by your description, it is possible. The whole issue started with trying to get printing through a remote Linksys print server, so that may qualify as a remote db. Beyond that, however, nothing I know of, just a standard laptop installation with normal stuff running locally

---

### Post by rogerw05465 on 2009-08-12
> **rogerw05465 said:**
> Not sure how to know what libraries are installed, but by your description, it is possible. The whole issue started with trying to get printing through a remote Linksys print server, so that may qualify as a remote db. Beyond that, however, nothing I know of, just a standard laptop installation with normal stuff running locally
Went ahead and ran sudo aptitude -f remove mfc6800lpr

Showed the same underlying dpkg error. Is there any way to find the archive it is complaining about (beginning of the thread)? There must be some way to pry under this error process...

---

### Post by rogerw05465 on 2009-08-13
> **rogerw05465 said:**
> Went ahead and ran sudo aptitude -f remove mfc6800lpr

Showed the same underlying dpkg error. Is there any way to find the archive it is complaining about (beginning of the thread)? There must be some way to pry under this error process...
Well, I learn what *not* to do...

Previous thought was to do this:
rogerw@rogerw-acer:~$ sudo aptitude -f remove mfc6800lpr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  **libpq5**{u} menu{u} mfc6800lpr 
0 packa pointges upgraded, 0 newly installed, 3 to remove and 182 not upgraded.
Need to get 0B of archives. After unpacking 2896kB will be freed.
Do you want to continue? [Y/n/?] 

And I did it, as I felt I had no option at this point. Now Thunderbird brings in mail - and eats it whole, with no trace! I see it arrive and disappear. Soooo...don't do this at home, kids!

---

### Post by rogerw05465 on 2009-08-13
> **rogerw05465 said:**
> Well, I learn what *not* to do...

Previous thought was to do this:
rogerw@rogerw-acer:~$ sudo aptitude -f remove mfc6800lpr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  **libpq5**{u} menu{u} mfc6800lpr 
0 packa pointges upgraded, 0 newly installed, 3 to remove and 182 not upgraded.
Need to get 0B of archives. After unpacking 2896kB will be freed.
Do you want to continue? [Y/n/?] 

And I did it, as I felt I had no option at this point. Now Thunderbird brings in mail - and eats it whole, with no trace! I see it arrive and disappear. Soooo...don't do this at home, kids!
Looks like we may have a cure. See the thread on "**Ubuntu will not fix broken packages"**

---

