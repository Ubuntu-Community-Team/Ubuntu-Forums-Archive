---
title: "Red Triangle with Exclamation mark."
date: 2010-08-19
forum: General Help
---

### Post by bulldog1 on 2010-08-19
Hi all.

This is my first post.

Recently, when trying to update, a red triangle appears in the top tool bar. Here is the message in full...

***The repository may no longer be available or could not be corrected because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preference is correct***

[I]Failed to fetch cdrom://Ubuntu 10.04 LTS_Lucid Lynx_-Release i386 (20100429)//dists/lucid/main/binary-i386/Packages.gz. PLease use apt-cdrom to make this CDROM recognised by Apt.apt-get update cannot be used to add new CD-ROMs.

Failed to fetch cdrom://Ubuntu 10.04 LTS_Lucid Lynx_-Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz. PLease use apt-cdrom to make this CDROM recognised by Apt.apt-get update cannot be used to add new CD-ROMs.

Some index files failed to download, they have been ignored, or old ones used instead.[/I]

I'am new to Ubuntu, so please pardon me if this is a simple problem

---

### Post by Elfy on 2010-08-19
System - Admin - Software Sources - untick the cdrom 

Reload

---

### Post by bulldog1 on 2010-08-19
Thank you very much. Working perfect now;)

---

### Post by dmursell on 2010-09-02
i have a similar problem but my message for the problematic update is this ,i think, anyone able to help ?

Failed to fetch [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/jaunty/main/binary-i386/Packages.gz](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/jaunty/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


thank you

---

### Post by valbaca on 2010-09-03
> **dmursell said:**
> i have a similar problem but my message for the problematic update is this ,i think, anyone able to help ?

Failed to fetch [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/jaunty/main/binary-i386/Packages.gz](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/jaunty/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


thank you
You have two ppa (personal packaged archives) for two different Ubuntu releases (jaunty and lucid).
Go to System > Administration > Software Sources > "Other Software" and uncheck the one that doesn't apply to your version of Ubuntu

---

### Post by Elfy on 2010-09-03
Seems that ppa is gone, so you will need to remove both of the entries - if you really need to use a ppa for vlc then you will need to use a different one.

Have a look here [http://ubuntuforums.org/showthread.php?t=1559242](http://ubuntuforums.org/showthread.php?t=1559242)

In future please start a thread of your own unless you are sure that the issue is the same - obviously not the case here.

---

