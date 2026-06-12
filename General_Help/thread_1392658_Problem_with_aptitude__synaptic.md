---
title: "Problem with aptitude / synaptic"
date: 2010-01-28
forum: General Help
---

### Post by colm.debarra on 2010-01-28
Hi,

I installed flight gear a while ago, but then saw I was running short of disk space so uninstalled it (install and uninstall were both through synaptic). 

Then I noticed that the flight gear directory was still in 
/usr/share/games so I deleted it manually
It turns out that these files belonged to a package called fgfs-base - a base flight gear lib (why did synaptic not delete this package along with flight gear - grrrr)
Anyway now that those files were deleted synaptic tells me that the fgfs package is in a very unstable state and refuses to delete / upgrade / install it so it's stuck and I can't seem to do anything with it.
Now I want to install flight gear again since my HD space issue is sorted, but the state of this package blocks everything.

Anyone know how to fix this ?

Cheers,
Colm

---

### Post by sisco311 on 2010-01-28
Try to fix the broken package:
```
sudo apt-get install -f
```

---

### Post by colm.debarra on 2010-01-28
Thanks for the reply. Tried that but it didn't help.
Gave the same error.

```
sudo apt-get install -f fgfs-base
[sudo] password for colm: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  fgfs-base
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/250MB of archives.
After this operation, 75.8MB of additional disk space will be used.
(Reading database ... 263399 files and directories currently installed.)
Preparing to replace fgfs-base 1.0.0-2 (using .../fgfs-base_1.9.0-1_all.deb) ...
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/fgfs-base_1.9.0-1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
ln: creating symbolic link `/usr/share/games/FlightGear/Timezone': No such file or directory
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fgfs-base_1.9.0-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by phillw on 2010-01-28
Also ```
sudo dpkg --configure -a
``` can help with an unhappy dpkg

Regards,

Phill.

---

### Post by colm.debarra on 2010-01-28
nope.

```
colm@sativa:~$ sudo dpkg --configure -a
dpkg: error processing fgfs-base (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 fgfs-base

```

---

### Post by sisco311 on 2010-01-28
> **colm.debarra said:**
> nope.

```
colm@sativa:~$ sudo dpkg --configure -a
dpkg: error processing fgfs-base (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 fgfs-base

```

Recreate the missing symbolic link, fix the package & remove it:
```
sudo mkdir -p /usr/share/games/FlightGear/
sudo ln -s -T /usr/share/zoneinfo/ /usr/share/games/FlightGear/Timezone
```

```
sudo apt-get install -f
sudo apt-get purge fgfs-base
sudo apt-get autoremove 
sudo apt-get update
```

It worked for me, it was fun. :)

---

### Post by colm.debarra on 2010-01-28
Hallelujiah !! That worked :)

Thanks a million ...........

---

### Post by sisco311 on 2010-01-28
> **colm.debarra said:**
> Hallelujiah !! That worked :)

Thanks a million ...........

You're welcome!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

