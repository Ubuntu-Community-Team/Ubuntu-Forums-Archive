---
title: "AMD Catalyst 11.3"
date: 2011-03-19
forum: General Help
---

### Post by hai2lp on 2011-03-19
Amd Catalyst 11.3 is out but not sure if it's work with Ubuntu Natty or not



Is anyone having some problem with ubuntu 10.10 using latest kernel and Ubuntu 11.04 cannot using Ati Catalyst fglrx driver

Please if anyone get luck using Catalyst 11.2 but working in Ubuntu 11.04

I really need the next AMD CATALYST 11.3

Please release it soon AMD ....

---

### Post by clhsharky on 2011-03-19
hai2lp

Help for 11.04 is in  Development & Programming > Natty Narwhal Testing and Discussion 
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

Fglrx does not support Ubuntu 11.04 yet, some time next month a new pre release Catalyst 11.4 should be released.

Ubuntu 10.10 with .37 kernel with Catalyst 11.3 does work.


Sharky

---

### Post by hai2lp on 2011-03-19
> **clhsharky said:**
> hai2lp

Help for 11.04 is in  Development & Programming > Natty Narwhal Testing and Discussion 
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

Fglrx does not support Ubuntu 11.04 yet, some time next month a new testing Catalyst 11.4 should be released.

Ubuntu 10.10 with .37 kernel with Catalyst 11.3 does work.


Sharky

is Amd Catalyst 11.3 already release ... coz i dont see there's in amd.com

---

### Post by clhsharky on 2011-03-19
hai2lp

> is Amd Catalyst 11.3 already release ... coz i dont see there's in amd.com
Not the final release, It gets updated around the 20th.
Catalyst 11.2 all ready supports .37 kernel.


Sharky

---

### Post by hai2lp on 2011-03-21
> **clhsharky said:**
> hai2lp


Not the final release, It gets updated around the 20th.
Catalyst 11.2 all ready supports .37 kernel.


Sharky

Where is amd catalyst 11.3,, 
why it take it so long....

---

### Post by Dr.Paneas on 2011-03-23
Where did yo find Catalyst 11.3 ?

---

### Post by hai2lp on 2011-03-23
> **Dr.Paneas said:**
> Where did yo find Catalyst 11.3 ?

What r u talking about?

I am still waiting for it

---

### Post by Yellow Pasque on 2011-03-23
> **hai2lp said:**
> Where is amd catalyst 11.3,, 
why it take it so long....

Repeatedly complaining about it on this forum will definitely make it come faster... :rolleyes:

---

### Post by Mark Phelps on 2011-03-23
> **Dr.Paneas said:**
> Where did yo find Catalyst 11.3 ?

Just checked the AMD site -- no Catalyst 11.3 Linux drivers -- yet.

---

### Post by hai2lp on 2011-03-24
natty narwal is comming ..

but why there's no announcement from amd about catalyst 11.3

---

### Post by blueridgedog on 2011-03-24
> **Mark Phelps said:**
> Just checked the AMD site -- no Catalyst 11.3 Linux drivers -- yet.

To me the logical choice is to support another vendor with my money.  I gave up ATI shortly after moving to Linux.

---

### Post by Yellow Pasque on 2011-03-24
> **hai2lp said:**
> natty narwal is comming ..

but why there's no announcement from amd about catalyst 11.3
..because it's not out yet. Wait patiently. It should be here sooner than later.

---

### Post by Yellow Pasque on 2011-03-24
> **blueridgedog said:**
> To me the logical choice is to support another vendor with my money.  I gave up ATI shortly after moving to Linux.
You can knock the quality of ATI's drivers, but they release them monthly (more than other GPU vendors). Seeing as how the month isn't over yet, there's an awful lot of crying/moaning..

---

### Post by gabbo81 on 2011-03-24
the amd cat 11.3 and the newer 11.4 preview will be out next week.
 
you can follow one of the catalyscreator on twitter 
 
[http://twitter.com/CatalystCreator](http://twitter.com/CatalystCreator)

---

### Post by Dr.Paneas on 2011-03-24
That's great news! The thing is that current fglrx catalyst 11.2 is broken with latest kernel 2.6.38 :(  I hope Catalyst 11.3 will fix dat :)

---

### Post by gabbo81 on 2011-03-29
amd cat 11.3 are out:)

---

### Post by mrmagos on 2011-03-29
Catalyst 11.3 dropped today, but there's still no support for kernel 2.6.38 :( Hopefully there will be a patch in the coming days, like there was for 10.12 so it would build against kernel 2.6.37.

---

### Post by hai2lp on 2011-03-29
where is AMD 11.3 ? 

i don't see in amd.com

---

### Post by clhsharky on 2011-03-30
hai2lp

> i don't see in amd.com 
[http://www2.ati.com/drivers/linux/ati-driver-installer-11-3-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-3-x86.x86_64.run)


Sharky

---

### Post by hai2lp on 2011-03-30
> **clhsharky said:**
> hai2lp


[http://www2.ati.com/drivers/linux/ati-driver-installer-11-3-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-3-x86.x86_64.run)


Sharky

Has anyone try it with latest kernel 2.6.38 / Ubuntu Natty ?

---

### Post by Yellow Pasque on 2011-03-30
> **hai2lp said:**
> Has anyone try it with latest kernel 2.6.38 / Ubuntu Natty ?
Don't bother. It won't work.

---

### Post by hai2lp on 2011-03-30
> **Temüjin said:**
> Don't bother. It won't work.


The new fglrx (ATI proprietary driver) is in Natty repos now.
That is actually not a Catalyst 11.4 release (there is no such release  yet, latest stable is 11.3), but a prerelease (fglrx 8.84).

See here:
[https://launchpad.net/ubuntu/natty/+...8.840-0ubuntu1]("https://launchpad.net/ubuntu/natty/+source/fglrx-installer/2:8.840-0ubuntu1")
It is claimed to support both xserver 1.10 and kernel 2.6.38.

It has been said to be a special prerelease edition for Canonical and Ubuntu-users.
See more info here:
[http://www.phoronix.com/scan.php?pag...item&px=OTI3MQ]("http://www.phoronix.com/scan.php?page=news_item&px=OTI3MQ")

---

### Post by Dr.Paneas on 2011-03-30
I've just installed Catalyst 11.3 on Ubuntu 10.10 . I followed the same formula as I did in the last time... but I see that Version is still 11.2 . Why ?

[ATTACH]187600[/ATTACH]

Sorry for the greek language. You can see that the version of driver says 11.2 instead of 11.3
Here is what I did : [http://drpaneas.com/?p=66](http://drpaneas.com/?p=66)  to install them. 

So.. what am I doing wrong ?

**EDIT: NEW link**: [http://linuxscriber.com/how-to-2/how-to-install-new-catalyst-11-3-on-ubuntu/](http://linuxscriber.com/how-to-2/how-to-install-new-catalyst-11-3-on-ubuntu/)

---

### Post by ak47suk1 on 2011-04-06
> **Dr.Paneas said:**
> I've just installed Catalyst 11.3 on Ubuntu 10.10 . I followed the same formula as I did in the last time... but I see that Version is still 11.2 . Why ?

[ATTACH]187600[/ATTACH]

Sorry for the greek language. You can see that the version of driver says 11.2 instead of 11.3
Here is what I did : [http://drpaneas.com/?p=66](http://drpaneas.com/?p=66)  to install them. 

So.. what am I doing wrong ?

Same problem happen to me as well. I tried removing + purging fglrx related package. Reboot. Got low graphics warning. following [http://drpaneas.com/?p=66](http://drpaneas.com/?p=66)  to install them. Still get Catalyst 11.2 as well.:confused:

---

### Post by PsyForce on 2011-04-08
I'm also still getting 11.2. I was hoping 11.3 would fix quite a few issues, including an annoying AMD Unsupported hardware watermark in the lower right corner. :-|

---

### Post by Yellow Pasque on 2011-04-08
CCC showing old Catalyst version means you didn't completely remove the old version: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx) . Make sure /etc/ati is empty before installing.

---

### Post by PsyForce on 2011-04-09
I've just performed the following commands as per 
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx) :

```
$ sudo sh /usr/share/ati/fglrx-uninstall.sh 
$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```

It didn't remove anything from /usr/share/ati/ nor from /etc/ati/  Am I missing something?

Anyways, I'm going to reinstall 11.3 anyways, since I don't want to end up without drivers on a restart. Maybe it will work anyways...

--edit--
I just restarted and still have CCC 11.2.

---

### Post by javajeff1 on 2011-04-09
Works perfect for me.

Fresh install of 10.10 64 bit > Then installed all Ubuntu Updates including kernel > Then installed Catalyst 11.3

Installing the AMD drivers before the kernel updates did not work for me.  I am happy.

---

### Post by PsyForce on 2011-04-14
Well, I followed all of the instructions here:

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

and here:

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

verbatim. I copy/pasted everything relevant into terminal directly. I didn't seem to mess anything up, but Catalyst Control Center still shows 11.2. Apparently this is because it often shows the wrong version?

Anyways, I tried fglrxinfo:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6600M Series
OpenGL version string: 4.1.10600 Compatibility Profile Context
```

and fgl_glxgears seems to work fine, so I'm guessing it worked? It still didn't remove the unsupported hardware watermark though. I even followed the instructions in that portion of the page. I guess I'll be waiting for 11.4...

---

### Post by Yellow Pasque on 2011-04-14
> I didn't seem to mess anything up, but Catalyst Control Center still shows 11.2. Apparently this is because it often shows the wrong version?
Yes, it happens when cruft from a previous install gets left behind in /etc/ati (which the fglrx installer/packaging script does by design as I recently discovered). As far as I can tell, it is only a superficial annoyance. I was contemplating adding a command to clear /etc/ati in the remove section of the wiki, but I'm going to hold off on that until I fully understand the ramifications of doing that.

---

### Post by PsyForce on 2011-04-15
Ok, good to know it's not just 'random'.  :rolleyes:

---

