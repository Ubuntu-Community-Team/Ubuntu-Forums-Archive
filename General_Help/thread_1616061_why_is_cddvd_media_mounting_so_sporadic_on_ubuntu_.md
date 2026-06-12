---
title: "why is cd/dvd media mounting so sporadic on ubuntu 10.04 for me?"
date: 2010-11-07
forum: General Help
---

### Post by BcRich on 2010-11-07
hi 
for some reason/s in ubuntu 10.04 lucid i get the most sporadic and seemingly random results for mounting cd's or dvd's. most of the time they just don't mount and i have to reboot my computer and then they seem to mount. 
I've been reading the forums and there seems to be many, many many..... posts about this problem in 10.04 as it would seem many people are having issues relating to this.
i've tried every thing i can think of to resolve it (although i'm still a bit of a newbie so that might not mean much to the advanced users out there).
my system is up to date, i've tried the "boot up with cd/dvd in the drive option", switching my boot order in bios, adding a /media/cdrom0 dir and using mountmanager to automount that drive at bootup but none of these options work for me.
heres a link to a bug that seems to be similar
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/546992](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/546992)
and here's two more threads that are also similar
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1469627](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1469627)
[http://ubuntuforums.org/showthread.php?t=1468035](http://ubuntuforums.org/showthread.php?t=1468035)
just so that i can't be accused of not having "done my homework"
my installation of 10.04 is a fresh install so i don't see why i should be having the fstab issue noted in the posts but maybe i'm wrong.
here's what ```
dpkg -l hal
``` returns
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  hal            0.5.14-0ubuntu Hardware Abstraction Layer
```
if there is someone's expertise that i can draw upon i would be most sincerely appreciative. in fact that is such an understatement having this issue resolved would be as amazing, for me, as the entire world suddenly becoming friends (...like in the non-facebook kinda way).

---

### Post by oboedad55 on 2010-11-10
I see your post is a couple of months old, I found it Googling the same problem with Lucid. I've tried every fix in the book and still no love. If you ever figure this out please post here! I don't have this problem with Maverick but I have sound weirdness instead, which for me is worse.

---

### Post by BcRich on 2010-11-11
*******************************************UPDATE*******************************************************
       *******please disregard the following 3 suggestions as they are now outdated**************
*************************************** see next post  ************************************

hi oboedad55
this thread is only about 3 days old :) but i've been looking for a fix to this issue for more than a month and have not been able to find any solutions. currently my cd/dvd drive is still sporadically working in 10.04. since i have a duel boot system with ubuntu 9.04 in which my cd drive works perfectly i can safely conclude that it is not a hardware issue.
here's some suggestions (none of which are really solutions but might help improve the situation somewhat) if you haven't already tried them,
 1. Boot your computer with a CD/DVD in the drive and/or
2. change the boot order of your cd/dvd drive to be second after your first harddrive and/or
3. install mountmanager 0.2.6
3a.create a dir in /media/ called cdrom0 so you should have a directory structure like /media/cdrom0
3b. in mountmanager select your cd/dvd drive (which has the identifier sr0 on my computer) and in the mount point input field add the path to the directory you just created eg /media/cdrom0
3c. in the general section you can check the box that says "Mount the partition during startup" however if you don't have a cd/dvd in the drive when you start your computer, your startup time will increase as the system tries to mount media that does not exist and you will be presented with a screen that says something to the effect of press S to skip mounting this partition at startup. simply pressing s will continue booting as per normal. but i must warn you that option 3 is a bit of an "ugly" hack as it makes your system look "buggy" at startup and it does not work all the time.
sorry i couldn't be of more assistance, that's about as far as i've come with this problem. if there is anyone out there that has a better solution i'm sure there are many people in the community that would absolutely love to hear it :)
all the best

---

### Post by oboedad55 on 2010-11-11
Thanks for the reply. I apparently have found a solution. I installed kernel 2.6.35 and the CD drive has been working for many hours now, which has never been the case. Here is where you can get it: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/)

Please post back with your results.

---

### Post by BcRich on 2010-11-12
hi oboedad55
thank you very much for your reply. I've just tried the new kernel version you recommended and my cd/dvd drive usage seems to have been restored to normal :)
I'll post back here if anything changes.
BTW it might also be worth noting that this new kernel also cleared up an issue i was having with my usb modem being loaded as a cd drive. now my modem does not appear as a drive on my desktop, which is exactly the way it has always been since i started using it with ubuntu in 8.04. So i'm much more confident in this solution you've presented.
Finally when i tried the mountmanager solution in option 3 of my preceding post, mountmanager modified my fstab file so in oder to correct this i had to comment out the extra line it added to the file and now i don't have to press "s" during startup (to skip mounting)
```
#/dev/sr0 /media/cdrom0 udf,iso9660 defaults 0 0
UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a /media/320GB ext3 defaults 0 1
UUID=17b48cc8-3666-4e34-ab28-09d51354b6a4 / ext4 defaults 0 1
UUID=b92cf0ff-7776-476e-a531-a073d8fbf468 swap swap sw 0 0
UUID=455c84a2-4f62-4761-bde6-7ff38fff7011 swap swap sw 0 0
```
so my fstab file now looks like this and my system seems to be working normally.
thanks again for your help oboedad55, i'm sure many people will be grateful for you previous post!
all the best

---

### Post by oboedad55 on 2010-11-12
BcRich, man, I'm real glad to hear that. I've been trying every weird "fix" under the sun for weeks with no love. My fingers are worn out from Googling variations on this problem. A guy on the Mint forums suggested the new kernel but it wasn't until this latest one that anything changed. I guess you figured out that CDs don't need fstab entries any more to work. I messed around with that to no avail as well. In any case I'm thrilled it worked for you too and I hope that this will help someone else with the same issue.

---

### Post by BcRich on 2010-11-13
hi oboedad55
I hear you :) i've also grappled with this problem and "pseudo-fixes" (no offense to those that have made genuine suggestions to fixing this problem, working or not). it's seems like your recommendation is a winner. I've tried cd's and dvd's in the drive, booted and rebooted several time and still the drive works. i've also tried mounting my 10.04 repository discs (which have not worked since I got them as sources in synaptic) and even they are working!
Most excellent, I cannot thank you enough for your post, oboedad55.
thanks a million, you're making some ubuntu'ers very happy :)

---

### Post by oboedad55 on 2010-11-13
Woohoo! Weeks of Googling paid off. Please go and thank the guy on this forum who got me started. It was his idea to mess with new kernels. [http://forums.linuxmint.com/viewtopic.php?f=90&t=58374](http://forums.linuxmint.com/viewtopic.php?f=90&t=58374)

---

### Post by DaveBentham on 2010-11-15
Hi,
I have been having this problem too. But when I tried the 2.6.35 kernel install suggested here, it breaks my GDM and it leaves me with a textual login... Manual attempts to start it claim no user in seat-id or some such error. I am well disappointed with this saga.

Also, if you haven't seen it, it may be due for a proper lucid kernel update soon as seen here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605716](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605716).

---

### Post by oboedad55 on 2010-11-15
> **DaveBentham said:**
> Hi,
I have been having this problem too. But when I tried the 2.6.35 kernel install suggested here, it breaks my GDM and it leaves me with a textual login... Manual attempts to start it claim no user in seat-id or some such error. I am well disappointed with this saga.

Also, if you haven't seen it, it may be due for a proper lucid kernel update soon as seen here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605716](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605716).

Did you install both linux-header debs? The worst that happens is you boot into your old kernel and remove the new one.

---

### Post by DaveBentham on 2010-11-15
No, I only installed the linux-image. As I understand it, the headers are  a bunch of C header files appropriate to the installed kernel. Had that image worked without breaking anything else, I would of gone on to install them, for completeness, but I rarely compile source.

I find it bizarre that GDM, a binary executable, relies on in-situ kernel C header files to function. Please enlighten me if I am mistaken.

The new kernel itself did boot up, just with no GDM/Gnome, and I was able to remove it easily and restore my pc.

---

### Post by oboedad55 on 2010-11-15
> **DaveBentham said:**
> No, I only installed the linux-image. As I understand it, the headers are  a bunch of C header files appropriate to the installed kernel. Had that image worked without breaking anything else, I would of gone on to install them, for completeness, but I rarely compile source.

I find it bizarre that GDM, a binary executable, relies on in-situ kernel C header files to function. Please enlighten me if I am mistaken.

The new kernel itself did boot up, just with no GDM/Gnome, and I was able to remove it easily and restore my pc.

You may be right, but I installed the headers as without them the kernel would only boot to a command prompt.

---

### Post by DaveBentham on 2010-11-15
Well, 5 points to you oboedad55! I reinstalled the 2.6.35 image and headers, as you suggested, and GDM/Gnome seem fine now, as do CD mounts. Still seems bizarre to me though that the headers have that effect. Nevermind: it works.

Thankyou
Dave

---

### Post by oboedad55 on 2010-11-15
> **DaveBentham said:**
> Well, 5 points to you oboedad55! I reinstalled the 2.6.35 image and headers, as you suggested, and GDM/Gnome seem fine now, as do CD mounts. Still seems bizarre to me though that the headers have that effect. Nevermind: it works.

Thankyou
Dave

Glad it works for you, but only 5 points? I think that's worth at least 7 for all the time I wasted on this problem, LOL.

---

### Post by col48 on 2010-11-15
oboedad, you forgot the currency conversion

Poole points are like Devon miles, bigger than anyone else's!

---

### Post by oboedad55 on 2010-11-15
> **col48 said:**
> oboedad, you forgot the currency conversion

Poole points are like Devon miles, bigger than anyone else's!

OK, gotcha. I'm just glad it worked for you. I spent weeks fiddling with the problem and Googled it to death. It was a guy on a Mint forum who suggested it. I was as skeptical as you. When I posted back that it had worked another guy chimed in to tell me it was only the process of installing a new kernel(!) that fixed the problem. Well, were that true then the other two kernels I installed should have fixed it but they didn't. Here is the Mint thread if you're curious;
[http://forums.linuxmint.com/viewtopic.php?f=90&t=58374](http://forums.linuxmint.com/viewtopic.php?f=90&t=58374)

---

