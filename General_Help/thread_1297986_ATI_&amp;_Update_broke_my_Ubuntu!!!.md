---
title: "ATI &amp; Update broke my Ubuntu!!!"
date: 2009-10-22
forum: General Help
---

### Post by [=Vion=] on 2009-10-22
So I recently installed 9.04 and today I installed the ATI driver. Im running an HD4850 and there where some issues. After I installed the drivers and rebooted the screen went blank so I rebooted again and everything was fine. I then installed all the available updates and rebooted but now the blank screen went back again so I went into safe mode cause I thought it was like Windows safe mode but no. There was an option that would "attempt to fix graphics problems" so I chose that one. It said something about x org and now ubuntu freezes at the splash screen. Help me plz!

---

### Post by phillw on 2009-10-22
try rebuilding the x-org ....

sudo dpkg-reconfigure xserver-xorg
Try the various options.

There is some further stuff Xorg here ...

[https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge)

Regards,

Phill.

---

### Post by [=Vion=] on 2009-10-22
> **phillw said:**
> try rebuilding the x-org ....

sudo dpkg-reconfigure xserver-xorg
Try the various options.

There is some further stuff Xorg here ...

[https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge)

Regards,

Phill.

Thats what im trying to do but I have no idea how to access the commend prompt at boot up or in safe mode.

So how would one do so???

---

### Post by screaminfakah on 2009-10-22
There is an option to drop to shell prompt with and without networking when you boot to Recovery.
I tried ATIs drivers from their website and it screwed everything up.  I went with Ubuntu's ATI restricted drivers and everything was fine.

---

### Post by tarps87 on 2009-10-22
Either ctrl+alt+fn   (fn = f1 to f6)
or
Hit escape when you get to the boot loader and select the recovery mode option, then boot into root shell

---

### Post by [=Vion=] on 2009-10-22
Ok so i just did that and went through some windows entering some options but nothing has changed. netx I will try entering this : aticonfig --initial -f and then I will try completely deleting the drivers with : apt-get remove fglrx*

---

### Post by [=Vion=] on 2009-10-22
I entered aticonfig --initial -f and now I only get a blank screen instead of the whole weird graphical glitch freeze. I guess I will have to delete.

---

### Post by [=Vion=] on 2009-10-22
Ok s oI did all the above and after deleting the drivers not it says something about a problem with xorg and takes me to a daignose window. after I exit it takes me to my login window with one exception....... via command prompt so i log in and it takes me to my desktop......via command... So what do I do now???

---

### Post by [=Vion=] on 2009-10-22
just finished reconfiguring xserver xorg and everthything is back to normal except for the fact that I no longer have video drivers. What do I do now... I have to run compiz but cant without drivers...???

---

### Post by screaminfakah on 2009-10-22
Go to hardware drivers in the administration menu and enable the ATI driver there.

---

### Post by [=Vion=] on 2009-10-22
the drivers dont show up there.... hmmm guess i will have to reinstall the manual way. Hope this doesnt happen again.


Thank you all for helping me. I greatly apreciate it :KS

---

### Post by phillw on 2009-10-22
There is a wiki on using the restricted drivers here ...

[https://help.ubuntu.com/community/RestrictedDrivers](https://help.ubuntu.com/community/RestrictedDrivers)

Hope it helps,

Phill.

---

### Post by Zoot7 on 2009-10-22
Here's a good guide to get the fglrx driver set up under Jaunty using a package based install.
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide")
Using this is what got Catalyst 9.8 for my HD4870 up and running pretty much perfectly under Jaunty.

---

### Post by markbuntu on 2009-10-22
It is abolutely critical to remove all old drivers and their kernel modules before installing a new driver. Failure to do this can cause blank screen or worse on kernel updates because the kernel will detect more than one set of driver kernel modules and so will not build any.

The guide in the post above tells you how to do this properly.

I have not had a kernel update fail on me running two versions of Hardy (32 and 64 bit) and Jaunty 64 bit using fglrx since the 8.6 (9.4 for Jaunty) driver once I started removing old drivers before installing new ones.

---

### Post by izg on 2009-10-24
I have a similar issue.

Try these steps:
[http://ubuntuforums.org/showthread.php?p=7996934](http://ubuntuforums.org/showthread.php?p=7996934)

Currently, trying option 3. Option 4 didn't work, even with recently released drivers by ati (10/22/2009)

good luck.

---

