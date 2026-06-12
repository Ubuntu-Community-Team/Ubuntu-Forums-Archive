---
title: "apt-get install hangs when unpacking packages"
date: 2011-06-18
forum: General Help
---

### Post by iconoclast hero on 2011-06-18
Here is what I've already done, I decided to start a new thread because the title was not very descriptive:

[http://ubuntuforums.org/showthread.php?p=10953296#post10953296](http://ubuntuforums.org/showthread.php?p=10953296#post10953296)
This is where I'm at now... It seems that no matter what I try to install, it hangs when it tries to unpack...
```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  flashplugin-installer flashplugin-nonfree grub-common grub-pc
  icedtea-6-jre-cacao icedtea6-plugin libxml2 libxml2-utils openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib python-libxml2
  ttf-symbol-replacement-wine1.3 wine1.3
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 50.3MB of archives.
After this operation, 319kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main ttf-symbol-replacement-wine1.3 all 1.3.22-0ubuntu1~ppa1~maverick1 [59.4kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main libxml2 i386 2.7.7.dfsg-4ubuntu0.2 [824kB]
Get:3 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main wine1.3 i386 1.3.22-0ubuntu1~ppa1~maverick1 [12.3MB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse flashplugin-installer i386 10.3.181.26ubuntu0.10.10.1 [20.6kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse flashplugin-nonfree i386 10.3.181.26ubuntu0.10.10.1 [1,768B]
Get:6 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main grub-pc i386 1.98+20100804-5ubuntu3.3 [788kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main grub-common i386 1.98+20100804-5ubuntu3.3 [1,547kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main libxml2-utils i386 2.7.7.dfsg-4ubuntu0.2 [89.5kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main icedtea6-plugin i386 6b20-1.9.8-0ubuntu1~10.10.1 [78.7kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main icedtea-6-jre-cacao i386 6b20-1.9.8-0ubuntu1~10.10.1 [417kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main openjdk-6-jre-lib all 6b20-1.9.8-0ubuntu1~10.10.1 [6,156kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main openjdk-6-jre-headless i386 6b20-1.9.8-0ubuntu1~10.10.1 [27.5MB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main openjdk-6-jre i386 6b20-1.9.8-0ubuntu1~10.10.1 [251kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main python-libxml2 i386 2.7.7.dfsg-4ubuntu0.2 [217kB]
Fetched 50.3MB in 1min 23s (599kB/s)                                           
Preconfiguring packages ...
(Reading database ... 159122 files and directories currently installed.)
Preparing to replace ttf-symbol-replacement-wine1.3 1.3.21-0ubuntu1~maverick1~ppa2 (using .../ttf-symbol-replacement-wine1.3_1.3.22-0ubuntu1~ppa1~maverick1_all.deb) ...
Unpacking replacement ttf-symbol-replacement-wine1.3 ...

```

---

### Post by Bucky Ball on 2011-06-18
Did you run 'sudo apt-get update' ***first***? This is a must. ;)

---

### Post by iconoclast hero on 2011-06-18
> **Bucky Ball said:**
> Did you run 'sudo apt-get update' ***first***? This is a must. ;)
Of course...  This is the latest output (with the apt-get install upgrade hanging at unpack):
```
sudo apt-get update
.
.
.
Ign http://ppa.launchpad.net maverick/main Sources
Ign http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
Fetched 2,311B in 1s (1,935B/s)
W: Failed to fetch http://ppa.launchpad.net/acheck/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/acheck/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

As you can see, there are some issues in the update, but it doesn't seem like has been a problem with them before.  They are also not in my /etc/apt/sources.list so I don't know how to remove the incorrect launchpad links.

---

### Post by Bucky Ball on 2011-06-18
You haven't got Synaptic Package Manager open (or any other package manager) while you are attempting the update/upgrade?

---

### Post by iconoclast hero on 2011-06-18
> **Bucky Ball said:**
> You haven't got Synaptic Package Manager open (or any other package manager) while you are attempting the update/upgrade?

The /var/lib/dpkg/lock file is from another process that was running at the same time (sudo apt-get update).

I think it turns out that having a bad SD card in the card reader (which I'd previously run my ubuntu system from) was the issue.  That is why I wanted testdisk in the first place.  Now that I've removed it and rebooted, it seems to be working.

Very very odd...

Anyway, I think that was the issue... how it is related, I have no idea, but I'm going to mark the thread solved for now.

---

### Post by wildmanne39 on 2011-06-18
> **iconoclast hero said:**
> The /var/lib/dpkg/lock file is from another process that was running at the same time (sudo apt-get update).

I think it turns out that having a bad SD card in the card reader (which I'd previously run my ubuntu system from) was the issue.  That is why I wanted testdisk in the first place.  Now that I've removed it and rebooted, it seems to be working.

Very very odd...

Anyway, I think that was the issue... how it is related, I have no idea, but I'm going to mark the thread solved for now.Hi, I am glad you got it working, sorry I had to leave before you got it fixed but it was after 3 in the morning here and I needed to get some rest.

---

### Post by MikeEvans on 2011-06-24
I just had this issue on 10.10.  Unplugged all  USB devices but no good.  Rebooted to recovery mode, dropped to root prompt, updated from there with no problem.

---

