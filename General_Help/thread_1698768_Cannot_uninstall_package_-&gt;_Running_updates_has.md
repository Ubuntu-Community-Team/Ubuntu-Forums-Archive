---
title: "Cannot uninstall package -&gt; Running updates has become impossible!"
date: 2011-03-02
forum: General Help
---

### Post by Mickpunt on 2011-03-02
Hi,

I'm having some trouble with my Ubuntu 10.

In order to solve a certain problem - XBMC totally freezing up my system - I recently installed **linux-backports-modules-alsa-2.6.31-22-generic** as suggested by a member of the community.

This did not result in a more stable XBMC so I wanted to uninstall it. No way. Ubuntu doesn't let me... See what I try:

```
sudo apt-get purge linux-backports-modules-alsa-2.6.31-22-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-backports-modules-alsa-2.6.31-22-generic
0 upgraded, 0 newly installed, 1 to remove and 22 not upgraded.
1 not fully installed or removed.
After this operation, 6,480kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 225106 files and directories currently installed.)
Removing linux-backports-modules-alsa-2.6.31-22-generic ...
FATAL: Could not open '/boot/System.map-2.6.31-22-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.31-22-generic
Cannot find /lib/modules/2.6.31-22-generic
update-initramfs: failed for /boot/initrd.img-2.6.31-22-generic
dpkg: error processing linux-backports-modules-alsa-2.6.31-22-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-alsa-2.6.31-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Anybody have any solution to purge this package? I guess I must've installed it badly. But no matter what I can't clean this. The result is I cannot update Ubuntu anymore :icon_frown:

**Following are my OS details:**
Linux Distribution: Ubuntu 10.04.2 LTS, 2.6.32-28-generic-pae i686. Built on Dec 17 2010 ( SVN:35648 )
Architecture: i686

**System Hardware Specs**
See: [http://tweakers.net/gallery/282996?inv_id=114404#tab:inventaris](http://tweakers.net/gallery/282996?inv_id=114404#tab:inventaris)
HDD: Samsung EcoGreen F4EG HD204UI, 2TB
Case: Lian Li PC-V354
Keyboard: Enermax Aurora Micro Wireless
CPU: Intel Core i3 530
Blu-Ray: Samsung SH-B083L (8x, SATA-150, dual-layer, Zwart, Retail)
Power: be quiet! Straight Power BQT E7-CM-480W
RAM: Kingston HyperX KHX1600C9D3K2/4G
GPU: Asus ENGT240 Silent/DI/1GD3
Motherboard: Asrock H55M Pro

---

### Post by turtle153 on 2011-03-02
Run```
sudo apt-get install -f
```

---

### Post by Mickpunt on 2011-03-02
Nope, already tried it... same error:

```
sudo apt-get install -f
[sudo] password for mick:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-backports-modules-alsa-2.6.31-22-generic
0 upgraded, 0 newly installed, 1 to remove and 22 not upgraded.
1 not fully installed or removed.
After this operation, 6,480kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 225106 files and directories currently installed.)
Removing linux-backports-modules-alsa-2.6.31-22-generic ...
FATAL: Could not open '/boot/System.map-2.6.31-22-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.31-22-generic
Cannot find /lib/modules/2.6.31-22-generic
update-initramfs: failed for /boot/initrd.img-2.6.31-22-generic
dpkg: error processing linux-backports-modules-alsa-2.6.31-22-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-alsa-2.6.31-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any other suggestions?

---

### Post by turtle153 on 2011-03-02
I may have had a similar problem, after a clean install I was getting dpkg problems and after trying every package manager (Update Manager, Synaptic, apt-get etc...) I got told to look at a file and line number where the problem was a rouge $ symbol :S

Use a different manager and see if it directs you anywhere.

---

### Post by matt_symes on 2011-03-02
Hi

Open a terminal and type

```
ls /boot
```

```
ls /lib/modules/
```

```
dpkg -l | grep linux-backports-modules-alsa 
```

That is a small L above.

Post back the results.

Where did you get linux-backports-modules-alsa-2.6.31-22-generic from ? These are the only ones i could find with a search

```
matthew@matthew-laptop:~$ apt-cache search linux-backports-modules-alsa-2.6
linux-backports-modules-alsa-2.6.32-21-generic - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-21-generic-pae - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-22-generic - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-22-generic-pae - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-23-generic - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-23-generic-pae - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-24-generic - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-24-generic-pae - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-25-generic - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-25-generic-pae - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-26-generic - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-26-generic-pae - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-27-generic - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-27-generic-pae - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-28-generic - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-28-generic-pae - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-29-generic - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
linux-backports-modules-alsa-2.6.32-29-generic-pae - Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
matthew@matthew-laptop:~$ 
```

I am also using 10.04.2

Kind regards

---

### Post by Mickpunt on 2011-03-02
Hi matt_symes,

Thanks for helping out. Following are the results for your requests:

```
ls /boot

abi-2.6.32-26-generic-pae     config-2.6.32-27-generic-pae      initrd.img-2.6.32-27-generic-pae  System.map-2.6.32-27-generic-pae  vmcoreinfo-2.6.32-28-generic-pae
abi-2.6.32-27-generic-pae     config-2.6.32-28-generic-pae      initrd.img-2.6.32-28-generic-pae  System.map-2.6.32-28-generic-pae  vmlinuz-2.6.32-26-generic-pae
abi-2.6.32-28-generic-pae     grub                              memtest86+.bin                    vmcoreinfo-2.6.32-26-generic-pae  vmlinuz-2.6.32-27-generic-pae
config-2.6.32-26-generic-pae  initrd.img-2.6.32-26-generic-pae  System.map-2.6.32-26-generic-pae  vmcoreinfo-2.6.32-27-generic-pae  vmlinuz-2.6.32-28-generic-pae

```

```
ls /lib/modules/

2.6.32-26-generic  2.6.32-26-generic-pae  2.6.32-27-generic  2.6.32-27-generic-pae  2.6.32-28-generic  2.6.32-28-generic-pae

```

```
dpkg -l | grep linux-backports-modules-alsa

rH  linux-backports-modules-alsa-2.6.31-22-generic 2.6.31-22.24                                    Ubuntu supplied Linux modules for version 2.

```

I think I got the package from this site: [http://packages.ubuntu.com/karmic-updates/i386/linux-backports-modules-alsa-2.6.31-22-generic/download](http://packages.ubuntu.com/karmic-updates/i386/linux-backports-modules-alsa-2.6.31-22-generic/download)

I installed the package manually.

---

### Post by mikewhatever on 2011-03-02
Try this:
```
sudo dpkg --purge --force-all linux-backports-modules-alsa-2.6.31-22-generic
```

---

### Post by Mickpunt on 2011-03-02
Unfortunately... still no deal:

```
sudo dpkg --purge --force-all linux-backports-modules-alsa-2.6.31-22-generic
[sudo] password for mick:
(Reading database ... 225106 files and directories currently installed.)
Removing linux-backports-modules-alsa-2.6.31-22-generic ...
FATAL: Could not open '/boot/System.map-2.6.31-22-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.31-22-generic
Cannot find /lib/modules/2.6.31-22-generic
update-initramfs: failed for /boot/initrd.img-2.6.31-22-generic
dpkg: error processing linux-backports-modules-alsa-2.6.31-22-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-alsa-2.6.31-22-generic
```


Ubuntu keeps whining on "Could not open '/boot/System.map-2.6.31-22-generic': No such file or directory". Should I somehow create this folder so it can continue?

---

### Post by matt_symes on 2011-03-02
Hi

It's looking like the install of that package was unsuccessful. It is registered with dpkg but some of the files it is trying to remove with the post uninstall script do not exist and hence it is failing.

Can i suggest you back up your system first as these are kernel modules and it would be nice to have a fallback position if things go wrong.

Anyway we can start with the basics and get progressively tougher.

Open a terminal and type

```
sudo dpkg --configure -a
```

This may or may not work.

[B]EDIT:

```
sudo dpkg --purge --force-all linux-backports-modules-alsa-2.6.31-22-generic
```

That was going to be my next suggestion so the above will not work.[/B]

We could try to manually remove the package.

Kind regards

---

### Post by Mickpunt on 2011-03-02
I realized something by looking at where I got his package from!
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)**karmic-updates**/i386/linux-backports-modules-alsa-2.6.31-22-generic/download

I think I might have installed a Karmic (Ubuntu 9) package on my Ubuntu 10! Ouch... I guess this is bad news?

---

### Post by matt_symes on 2011-03-02
Hi

Karmic updates are not the best to use in lucid.

Open a terminal and type.

```
dpkg -L linux-backports-modules-alsa-2.6.31-22-generic
```

```
ls /var/lib/dpkg/info/linux-backports-modules-alsa*
```

Post both results back here.

Kind regards

---

### Post by Mickpunt on 2011-03-02
Hi,

I am currently backing up my system as suggested in [http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

Seems this will take a while :)

So started a second terminal to get your results:

```
mick@nasman:~$ dpkg -L linux-backports-modules-alsa-2.6.31-22-generic
Package `linux-backports-modules-alsa-2.6.31-22-generic' does not contain any files (!)

```

And...

```
mick@nasman:~$ ls /var/lib/dpkg/info/linux-backports-modules-alsa*
/var/lib/dpkg/info/linux-backports-modules-alsa-2.6.31-22-generic.list
/var/lib/dpkg/info/linux-backports-modules-alsa-2.6.31-22-generic.md5sums
/var/lib/dpkg/info/linux-backports-modules-alsa-2.6.31-22-generic.postinst
/var/lib/dpkg/info/linux-backports-modules-alsa-2.6.31-22-generic.postrm

```

I'm really happy you and everybody else are helping me out!

---

### Post by matt_symes on 2011-03-02
Hi

> **Mickpunt said:**
> Hi,

I am currently backing up my system as suggested in [http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

Seems this will take a while :)

So started a second terminal to get your results:

```
mick@nasman:~$ dpkg -L linux-backports-modules-alsa-2.6.31-22-generic
Package `linux-backports-modules-alsa-2.6.31-22-generic' does not contain any files (!)

```

And...

```
mick@nasman:~$ ls /var/lib/dpkg/info/linux-backports-modules-alsa*
/var/lib/dpkg/info/linux-backports-modules-alsa-2.6.31-22-generic.list
/var/lib/dpkg/info/linux-backports-modules-alsa-2.6.31-22-generic.md5sums
/var/lib/dpkg/info/linux-backports-modules-alsa-2.6.31-22-generic.postinst
/var/lib/dpkg/info/linux-backports-modules-alsa-2.6.31-22-generic.postrm

```

I'm really happy you and everybody else are helping me out!

First lets wait for your system to backup and then we can try this to manually purge it and rollback if you have problems.

> mick@nasman:~$ dpkg -L linux-backports-modules-alsa-2.6.31-22-generic
Package `linux-backports-modules-alsa-2.6.31-22-generic' does not contain any files (!)

You see above. Even dpkg is surprised by that :p

Open a terminal and type

```
sudo rm /var/lib/dpkg/info/linux-backports-modules-alsa-2.6.31-22-generic.postrm
sudo apt-get remove --purge linux-backports-modules-alsa-2.6.31-22-generic
```

Enter your password after the first command. It will not be echoed to the screen.

After that if any of these files are left manually delete them

```
/var/lib/dpkg/info/linux-backports-modules-alsa-2.6.31-22-generic.list
/var/lib/dpkg/info/linux-backports-modules-alsa-2.6.31-22-generic.md5sums
/var/lib/dpkg/info/linux-backports-modules-alsa-2.6.31-22-generic.postinst
```

Just to be on the safe side then run

```
sudo update-initramfs -u
sudo apt-get update
```

I have to sleep at some point soonish. However i will be awake for a little while longer.

Hope it goes well.

Kind regards

---

### Post by mikewhatever on 2011-03-02
Well done, matt_symes!=D>

---

### Post by Mickpunt on 2011-03-02
Ok Matt, here's what happened:

```
sudo rm /var/lib/dpkg/info/linux-backports-modules-alsa-2.6.31-22-generic.postrm
```

```
root@nasman:/# sudo apt-get remove --purge linux-backports-modules-alsa-2.6.31-22-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-backports-modules-alsa-2.6.31-22-generic
0 upgraded, 0 newly installed, 1 to remove and 22 not upgraded.
1 not fully installed or removed.
After this operation, 6,480kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 225106 files and directories currently installed.)
Removing linux-backports-modules-alsa-2.6.31-22-generic ...
```

Yay! Sending you a very big hug now :D

Now for the rest... apparently nothing left of the alsa backport
```
root@nasman:/# ls /var/lib/dpkg/info/linux-backports-modules-alsa*
ls: cannot access /var/lib/dpkg/info/linux-backports-modules-alsa*: No such file or directory

```

And

```
root@nasman:/# sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.32-28-generic-pae
root@nasman:/# sudo apt-get update
Hit http://nl.archive.ubuntu.com lucid Release.gpg
Ign http://nl.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://nl.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://nl.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://nl.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:1 http://nl.archive.ubuntu.com lucid-updates Release.gpg [198B]
Ign http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://nl.archive.ubuntu.com lucid Release
Get:2 http://nl.archive.ubuntu.com lucid-updates Release [44.7kB]
Get:3 http://security.ubuntu.com lucid-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ lucid/main Translation-en_US
Get:4 http://security.ubuntu.com lucid-security Release [44.7kB]
Hit http://ppa.launchpad.net lucid Release
Hit http://nl.archive.ubuntu.com lucid/main Packages
Hit http://nl.archive.ubuntu.com lucid/restricted Packages
Hit http://nl.archive.ubuntu.com lucid/main Sources
Hit http://nl.archive.ubuntu.com lucid/restricted Sources
Hit http://nl.archive.ubuntu.com lucid/universe Packages
Hit http://nl.archive.ubuntu.com lucid/universe Sources
Hit http://nl.archive.ubuntu.com lucid/multiverse Packages
Hit http://nl.archive.ubuntu.com lucid/multiverse Sources
Get:5 http://nl.archive.ubuntu.com lucid-updates/main Packages [453kB]
Hit http://ppa.launchpad.net lucid/main Sources
Get:6 http://security.ubuntu.com lucid-security/main Packages [150kB]
Hit http://ppa.launchpad.net lucid/main Packages
Get:7 http://nl.archive.ubuntu.com lucid-updates/restricted Packages [3,240B]
Get:8 http://nl.archive.ubuntu.com lucid-updates/main Sources [182kB]
Get:9 http://nl.archive.ubuntu.com lucid-updates/restricted Sources [1,443B]
Get:10 http://nl.archive.ubuntu.com lucid-updates/universe Packages [190kB]
Get:11 http://nl.archive.ubuntu.com lucid-updates/universe Sources [68.2kB]
Get:12 http://nl.archive.ubuntu.com lucid-updates/multiverse Packages [8,427B]
Get:13 http://nl.archive.ubuntu.com lucid-updates/multiverse Sources [4,369B]
Get:14 http://security.ubuntu.com lucid-security/restricted Packages [14B]
Get:15 http://security.ubuntu.com lucid-security/main Sources [47.4kB]
Get:16 http://security.ubuntu.com lucid-security/restricted Sources [14B]
Get:17 http://security.ubuntu.com lucid-security/universe Packages [64.8kB]
Get:18 http://security.ubuntu.com lucid-security/universe Sources [19.3kB]
Get:19 http://security.ubuntu.com lucid-security/multiverse Packages [1,995B]
Get:20 http://security.ubuntu.com lucid-security/multiverse Sources [651B]
Fetched 1,284kB in 0s (1,398kB/s)
Reading package lists... Done

```

Me so happy! Sleep tight Matt :)

@mikewhatever: linux-backports-modules-alsa-2.6.31-22-generic.postinst does not exist anymore.

---

### Post by matt_symes on 2011-03-02
Hi

Glad it is fixed. 

I don't know about your XMBC issues but if you do want to try to install linux-backports-modules-alsa-2.6..... try one of the ones in synaptic

linux-backports-modules-alsa-2.6.32....

and make sure it's a generic-pae if that's the kernel you have.

Maybe the advise from the other poster will fix that issue as well.

Kind regards

---

