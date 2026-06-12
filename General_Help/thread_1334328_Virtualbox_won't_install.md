---
title: "Virtualbox won't install"
date: 2009-11-22
forum: General Help
---

### Post by Grozzy on 2009-11-22
Hi!
First I tried to install virtualbox OSE with no luck.
Then I tried to install the PUEL version with no luck there eighter.

All I get is this:

```
 * No suitable module for running kernel found
                                                                         [[COLOR=Red]fail[/COLOR]]
invoke-rc.d: initscript virtualbox-ose, action "restart" failed.

Setting up virtualbox-ose-source (3.0.8-dfsg-1ubuntu1) ...
Adding modules to DKMS build system
Doing initial module builds

Error! Your kernel source for kernel 2.6.28-16-generic cannot be found at
/lib/modules/2.6.28-16-generic/build or /lib/modules/2.6.28-16-generic/source.
dpkg: error processing virtualbox-ose-source (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up virtualbox-ose-qt (3.0.8-dfsg-1ubuntu1) ...

Processing triggers for menu ...
Errors were encountered while processing:
 virtualbox-ose-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Threre's something with the headers but i can't install the version that it claims not found..

Regards
Grozzy

---

### Post by corncob on 2009-11-22
I installed VirtualBox from the .deb file on [http://www.virtualbox.com](http://www.virtualbox.com) without errors.  My problem ( [http://ubuntuforums.org/showthread.php?t=1331610](http://ubuntuforums.org/showthread.php?t=1331610) ) was that the launcher didn't show up in the Applications/System Tools menu but a hard reboot (turning the computer off for several hours) fixed that.

---

### Post by Diabolis on 2009-11-22
Try after installing this:
```
sudo apt-get install linux-headers
```

---

### Post by Diabolis on 2009-11-22
> **corncob said:**
> I installed VirtualBox from the .deb file on [http://www.virtualbox.com](http://www.virtualbox.com) without errors.  My problem ( [http://ubuntuforums.org/showthread.php?t=1331610](http://ubuntuforums.org/showthread.php?t=1331610) ) was that the launcher didn't show up in the Applications/System Tools menu but a hard reboot (turning the computer off for several hours) fixed that.

This should have fixed it too:
```
update-menus
```

---

### Post by Grozzy on 2009-11-22
**sudo apt-get install linux-headers:**

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.31-9-rt 2.6.31-9.152
  linux-headers-2.6.31-14-generic-pae 2.6.31-14.48
  linux-headers-2.6.31-14-generic 2.6.31-14.48
  linux-headers-2.6.31-14-386 2.6.31-14.48
  linux-headers-2.6.31-14 2.6.31-14.48
You should explicitly select one to install.
E: Package linux-headers has no installation candidate

```

I can't see the 2.6.28-16-generic that it wants :/

---

### Post by Diabolis on 2009-11-22
Thats strange, it should be asking for the version of the kernel that you are running.

Find out which is your version and try with those linux-headers.
```
uname -r
```

---

### Post by Grozzy on 2009-11-22
Hah...
uname -r gives me "2.6.28-16-generic" and that is the header that Virtualb wants.
I must say that I don't understand anything now :P

---

### Post by Diabolis on 2009-11-22
apt-get offers you to install karmic koala headers, but uname shows a previous version of the kernel :-S

Something is not right, is your system fully updated?

Also still try this:
```
sudo apt-get install linux-headers-2.6.28-16-generic
```

---

### Post by Grozzy on 2009-11-22
Yes I have updated the system.
I'm starting to think that there's some repos missing because everytime I try to intall a header this comes:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-<package>

In "Software sources" I used to download from a server from Finland, I changed it to main server, and in the "Other software" tab I was using only two sources (Virtualbox sources and some Google chrome source). Could it actually be that there are missing repositories?

---

### Post by Grozzy on 2009-11-22
Okey, I think I've found the sulotion.
My GRUB menu.lst was not updated so I have been using an old kernel. I did just boot the newest kernel and now everything works!
My sound is working now too, it didn't work before :P

Thanks Diabolis for the quick replies!

---

