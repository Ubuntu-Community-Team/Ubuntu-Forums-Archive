---
title: "Latest upstart update unresolvable dependency"
date: 2011-02-01
forum: General Help
---

### Post by Fraoch on 2011-02-01
Is anyone else seeing this with the update today from upstart 0.6.6-3 to 0.6.6-4?

```
upstart:
  Breaks: libc6 (<2.12.1-0ubuntu10.2) but 2.12.1-0ubuntu10.1 is to be installed
```

Should I force this or is it a universal issue and should I wait for it to be resolved?

---

### Post by jimmyjones on 2011-02-01
Wondering the same.

You're not the only one.

---

### Post by chesterman on 2011-02-01
same here

---

### Post by imbjr on 2011-02-01
Well I avoided upgrading upstart, but then I saw this:

```

Installing new version of config file /etc/init/portmap.conf ...
portmap start/running, process 2900
There are RPC services which were registered with the portmapper
before the configuration was changed.
You need to manually restart them in order for the changes to take effect.
Current registered services:
------------------------------------------------
    100021    1   udp  50441  nlockmgr
    100021    3   udp  50441  nlockmgr
    100021    4   udp  50441  nlockmgr
    100021    1   tcp  41635  nlockmgr
    100021    3   tcp  41635  nlockmgr
    100021    4   tcp  41635  nlockmgr
    100024    1   udp  43803  status
    100024    1   tcp  49823  status
------------------------------------------------

```

I can't seem to find any information on how to restart those services, without resorting to a reboot.

---

### Post by Bob63 on 2011-02-01
I've got it too. I wouldn't force it as yet; wait for some more knowledgeable input.

It's odd that it wants to regress libc6.

---

### Post by Fraoch on 2011-02-01
Thanks for the advice everyone.

> **Bob63 said:**
> I've got it too. I wouldn't force it as yet; wait for some more knowledgeable input.

It's odd that it wants to regress libc6.

Yes, I'll leave it for now.

libc6 is a very important package, doesn't all code written in C depend on it?  I wouldn't want to mess with it.

Kind of looks like just a typo, that the older version of libc6 was specified.  libc6 was upgraded fairly recently (Jan. 12), could it be possible that 2.12.1-0ubuntu10.1 was the most current version at the time the developer(s) worked on upstart?

I've seen things like this happen from time to time - they usually get resolved in a day or two.

---

### Post by w0jrl on 2011-02-01
I'm glad I'm not the only one! I honestly thought I broke something.

Thanks,
Jeremy

---

### Post by daniel.kullmann on 2011-02-01
The libc6 version 2.12.1-0ubuntu10.2 is available from the maverick-proposed repository. This repository is by default deactivated. 

```

$ apt-cache policy libc6
libc6:
  Installed: 2.12.1-0ubuntu10.2
  Candidate: 2.12.1-0ubuntu10.2
  Version table:
 *** 2.12.1-0ubuntu10.2 0
        500 http://dk.archive.ubuntu.com/ubuntu/ maverick-proposed/main i386 Packages
        100 /var/lib/dpkg/status
     2.12.1-0ubuntu10.1 0
        500 http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ maverick-security/main i386 Packages
     2.12.1-0ubuntu6 0
        500 http://dk.archive.ubuntu.com/ubuntu/ maverick/main i386 Packages

```[B]Update:
[/B]I just updated to the latest version, and restarted the computer. Everything seems to work fine...

I guess the dependence on the libc6 version was an oversight by the person who created the upstart package.

---

### Post by bichopro on 2011-02-01
same problem here

ubuntu 64 with unity

---

### Post by hanzgroove on 2011-02-01
+1 on this issue. I'm waiting to see if the package is updated to resolve the problem.

---

### Post by jimmyjones on 2011-02-01
> **daniel.kullmann said:**
> The libc6 version 2.12.1-0ubuntu10.2 is available from the maverick-proposed repository. This repository is by default deactivated. 

```

$ apt-cache policy libc6
libc6:
  Installed: 2.12.1-0ubuntu10.2
  Candidate: 2.12.1-0ubuntu10.2
  Version table:
 *** 2.12.1-0ubuntu10.2 0
        500 http://dk.archive.ubuntu.com/ubuntu/ maverick-proposed/main i386 Packages
        100 /var/lib/dpkg/status
     2.12.1-0ubuntu10.1 0
        500 http://dk.archive.ubuntu.com/ubuntu/ maverick-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ maverick-security/main i386 Packages
     2.12.1-0ubuntu6 0
        500 http://dk.archive.ubuntu.com/ubuntu/ maverick/main i386 Packages

```[B]Update:
[/B]I just updated to the latest version, and restarted the computer. Everything seems to work fine...

I guess the dependence on the libc6 version was an oversight by the person who created the upstart package.


Thanks, I updated libc6 from the repository. Rebooted.

Doesn't appear to have hurt anything, Cleared the dependency issue.

---

### Post by amrun on 2011-02-01
+1 on this. waiting for further updates as well.
:popcorn:

---

### Post by kgsuarez on 2011-02-01
I just ran into this problem on a new installation of Ubuntu 10.10 (actually Mint 10) and I'm glad (kind of) to see that I am not alone in this.

I take it that I should refrain from installing the new version of upstart until this is all resolved, yes?

---

### Post by Bob63 on 2011-02-01
> **kgsuarez said:**
> I just ran into this problem on a new installation of Ubuntu 10.10 (actually Mint 10) and I'm glad (kind of) to see that I am not alone in this.

I take it that I should refrain from installing the new version of upstart until this is all resolved, yes?
I'm on Mint 10 as well; I decided to wait. There are so many things dependent on libc6 that I decided to wait for a day or so (at least) and am monitoring this thread. My system is working fine as is - I'd hate to break it.

---

### Post by ptn107 on 2011-02-01
Easy fix...

Wait for a new upstart package that fixes the dependency problem.

---

### Post by Moloch85 on 2011-02-01
I noticed the problem too. I was enlightened by this link:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

*"The proposed updates are updates which are waiting to be moved into the recommended updates queue after some testing. "*

I guess the last version of libc6 is waiting to be moved in recommended updates, while the upstart update have just been moved in. Not a big issue, maybe they'll fix it in a couple of days. ^__^

---

### Post by hellslinger on 2011-02-01
+1 for having this exact same trouble. Thanks!

---

### Post by Primefalcon on 2011-02-02
> **hellslinger said:**
> +1 for having this exact same trouble. Thanks!
Same issue, I think I'll wait

---

### Post by simonthd on 2011-02-02
Same here... I think I will wait too...

---

### Post by guendalf on 2011-02-02
See [https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/672177/comments/76](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/672177/comments/76)
So just wait until the new libc6 version is reviewed and released, or you can review it yourself.

---

### Post by FighterZP on 2011-02-02
same problem - unable install ubuntu ((

---

### Post by Bob63 on 2011-02-02
The latest round of updates included libc6, and (for me, anyhow) upstart installed its update.

OP, if your system is fixed by this, don't forget to add [SOLVED] to the subject line.;)

---

### Post by FighterZP on 2011-02-02
OOO!!! Problem Solved!!!! Everything worked!

---

### Post by Primefalcon on 2011-02-02
I just checked my update manager and the issue is fixed, not that there was any issue, since the dependency checks did their job and stopped an update that could of caused issues, Cherrios to the Ubu devs

---

### Post by telemicus on 2011-02-02
'tis fixed as of this morning from what I can tell?

---

### Post by Fraoch on 2011-02-02
Yup, libc6 was updated this morning which resolved the upstart dependency issue, so I'm marking the thread as solved.  Someone just jumped the gun by a day.;)

---

### Post by kiddykoff on 2011-02-23
i'm still having a problem with upstart. I thought waiting was a good idea, but something didn't work for me. As far as i know, libc6 is at the latest version.

---

### Post by Bob63 on 2011-02-23
> **kiddykoff said:**
> i'm still having a problem with upstart. I thought waiting was a good idea, but something didn't work for me. As far as i know, libc6 is at the latest version.

According to synaptic, the current version is 2.12.1-0ubuntu10.2

---

### Post by kiddykoff on 2011-02-23
either apt-get lied to me or i was mistaken. i looked in synaptic and there are multiple versions available, however forcing the latest version causes a number of applications to be removed. will i just need to install them again?

---

### Post by Bob63 on 2011-02-23
> **kiddykoff said:**
> either apt-get lied to me or i was mistaken. i looked in synaptic and there are multiple versions available, however forcing the latest version causes a number of applications to be removed. will i just need to install them again?
Which applications?

---

### Post by kiddykoff on 2011-02-23
acroread
android-notifier-desktop
build-essential
comerr-dev
g++
g++-4.4
google-talkplugin
googleearth
ia32-libs
krb5-multidev
lib32asound2
lib32bz2-1.0
libgcc1
lib32ncurses5
lib32nss-mdns
lib32stdc++6
lib32v4l-0
lib32z1
libbluetooth-dev
libc6-dev
libc6-i386
libcups2-dev
libcupsimage2-dev
libexif-dev
libexpat1-dev
libfontconfig1-dev
libfreetype6-dev
libgcrypt11-dev
libglib2.0-dev
libgnutls-dev
libgphoto2-2-dev
libjpeg62-dev
libkrb5-dev
libmng-dev
libpng12-dev
libqt3-mt-dev
libsane-dev
libsnmp-dev
libssl-dev
libstdc++6-4.4-dev
libtiff4-dev
libtool
libusb-dev
libxft-dev
lsb-build-cc3
lsb-build-desktop3
nspluginwrapper
nvidia-current
picasa
python-dev
python2.6-dev
skype
wine1.2
zlib1g-dev

these items are breaking when i try to force the upgrade of libc6.

---

### Post by Bob63 on 2011-02-23
@kiddykoff,
That's very strange; I have a lot of the same things installed (meaning development libraries), but didn't have to go through all that when libc6 upgraded.

Otherwise, you system is up-to-date?

---

### Post by kiddykoff on 2011-02-23
i just ran sudo apt-get update and sudo apt-get upgrade and mysteriously there were some more updates found. (14)

upstart is still being held back.

---

### Post by Bob63 on 2011-02-23
upstart will continue to be held back until you/we get your libc6 issue figured out.

---

### Post by mlsquad on 2011-02-25
I'm in the same boat.  upstart is being held back.  Synaptic shows libc6 as being 2.11.1-0ubuntu7.7, while upstart is needing 2.11.1-0ubuntu7.8.  I tried switching the mirror from "Server for United States" to "Main server" and did an update, but libc6 is still at 2.11.1-0ubuntu7.7.  I tried doing a reinstall of libc6 as well, and that didn't do anything.  Any thoughts on what I need to do to get libc6 up to date, so that upstart can upgrade?

---

### Post by Bob63 on 2011-02-25
@kiddykoff & mlsquad,
I'm curious as to how your software sources are configured. My system (which is currently experiencing ***no*** difficulty), has the following selected:
Main
Upstream
Imported
Backported
Unstable

While I am using Mint 10, it is a Ubuntu Maverick variation. Check your sources and see if setting them similar to this and refreshing helps (exact namess may vary in Maverick).

My thinking is that the patched library may not be in the Main repo yet.

---

### Post by mlsquad on 2011-02-25
> **Bob63 said:**
> @kiddykoff & mlsquad,
I'm curious as to how your software sources are configured. My system (which is currently experiencing ***no*** difficulty), has the following selected:
Main
Upstream
Imported
Backported
Unstable

While I am using Mint 10, it is a Ubuntu Maverick variation. Check your sources and see if setting them similar to this and refreshing helps.
In Software Source, in the Ubuntu Software tab I have the following selected:
main
universe
restricted
multiverse

In the Updates tab I have
lucid-security
lucid-updates
lucid-proposed

---

### Post by Bob63 on 2011-02-25
It's been a while since I used standard Ubuntu; is there a backported? Based on my reading with other bug reports, sometimes the fixes are applied to the the development version (Natty in this case) first then backported.

---

### Post by Taniquetil on 2011-02-25
I was still having a blocked upstart and just solved the problem by  deleting a stray "/etc/apt/preferences" file. Seems like I created this  some time ago to get something from the "proposed" repository, and now  it messed up priorities between security and updates.

---

### Post by pbvijay on 2011-03-08
Taniquetil Thank you very much... the solution you provide solved the upstart issue ...

---

