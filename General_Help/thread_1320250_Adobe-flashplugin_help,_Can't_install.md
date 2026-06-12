---
title: "Adobe-flashplugin help, Can't install"
date: 2009-11-09
forum: General Help
---

### Post by DezentSwe on 2009-11-09
Hi,

When I try to install Adobe flash on my friends computer I get this query

```
$ sudo aptitude reinstall flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
flashplugin-installer is not currently installed, so it will not be reinstalled.
flashplugin-installer is not currently installed, so it will not be reinstalled.
The following partially installed packages will be configured:
  adobe-flashplugin 
0 packages upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

And also
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
```

She tried to install it her self and did something and I can't find the problem. So I'm wondering if you guys have a solution to my problem


Best Regards,
Dezent

---

### Post by _khAttAm_ on 2009-11-09
sudo apt-get install flashplugin-installer

---

### Post by MelDJ on 2009-11-09
or get the .deb package from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by DezentSwe on 2009-11-09
I've tried both of these and none of them work :/

---

### Post by _khAttAm_ on 2009-11-09
Also perform a 
sudo apt-get update
prior to
sudo apt-get install flashplugin-installer 
that should do it.

BTW, are you using amd64 or i386?

---

### Post by MelDJ on 2009-11-09
try typing this in terminal: sudo apt-get install -f

then install flash

---

### Post by DezentSwe on 2009-11-09
> **_khAttAm_ said:**
> Also perform a 
sudo apt-get update
prior to
sudo apt-get install flashplugin-installer 
that should do it.

BTW, are you using amd64 or i386?

i386, and it didn't work

> **MelDJ said:**
> try typing this in terminal: sudo apt-get install -f

then install flash

I've tried this as well, and it didn't work.

---

### Post by MelDJ on 2009-11-09
have you added the medibuntu repositery to your sources list?

---

### Post by _khAttAm_ on 2009-11-09
Did you play around with repositories lately? If thats the case, goto repos in synaptic and make sure multiverse and universe are checked. Then 
sudo apt-get update
sudo apt-get install flashplugin-installer

EDIT: Quit synaptic before you use apt-get or use synaptic to make installation.

---

### Post by DezentSwe on 2009-11-09
Thanks, that did it :)

---

