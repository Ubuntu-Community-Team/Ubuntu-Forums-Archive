---
title: "Installing Ubuntu 8 in Ubuntu 11"
date: 2012-03-07
forum: General Help
---

### Post by Earl-Grey on 2012-03-07
Hello there,

I would like to install Ubuntu 8 Hardy Heron and need some advice.

Firstly I cannont boot by CD and my bios doesn`t support USB boot.

At the moment I have Win7 and Ubuntu 11 installed and I would like to install Ubuntu 8 when I am using Ubuntu 11.

Please could somebody tell me how to do this? I can view the Ubuntu 8 CD when in Ubuntu 11 but there is not install exe.

:KS

---

### Post by raja.genupula on 2012-03-07
i think you can make it with WUBI installation .

---

### Post by Cheesemill on 2012-03-07
8.04 has reached End Of Life and isn't supported anymore, there are security risks with running such a system.

If you still want to carry on I don't think that you can install it from a running system, but there are probably ways to let you boot from USB using something like PLOP boot manager.

What can you boot from?

---

### Post by Earl-Grey on 2012-03-07
I could install Ubuntu 11 in win7 with Wubi. Ubuntu 8 doesnt have Wubi so I cannot do it that way.

---

### Post by Cheesemill on 2012-03-07
> **Earl-Grey said:**
> I could install Ubuntu 11 in win7 with Wubi. Ubuntu 8 doesnt have Wubi so I cannot do it that way.

Wubi for 8.04
[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

Although I still wouldn't recommend using a Ubuntu release that isn't supported anymore.

---

### Post by raja.genupula on 2012-03-07
hmm [http://www.howtogeek.com/howto/9142/easily-install-ubuntu-linux-with-windows-using-the-wubi-installer/](http://www.howtogeek.com/howto/9142/easily-install-ubuntu-linux-with-windows-using-the-wubi-installer/)

---

### Post by raja.genupula on 2012-03-07
> **Cheesemill said:**
> Wubi for 8.04
[http://sourceforge.net/projects/wubi/files/Wubi/Wubi-8.04.506/Wubi-8.04.1-rev506.exe/download](http://sourceforge.net/projects/wubi/files/Wubi/Wubi-8.04.506/Wubi-8.04.1-rev506.exe/download)

Although I still wouldn't recommend using a Ubuntu release that isn't supported anymore.

oops! i am a bit late . Yeah i agree with you . 

@Op tell us ,why you wanna install Ubuntu 8.04 in your System , is there specific reason ?

---

### Post by 3Miro on 2012-03-07
Wubi should work, but neither Ubuntu 8.04 nor 8.10 should be used as main systems anymore by anyone. If you want to just pay with old versions of Ubuntu, then it is best to use VirtualBox (available for both Windows and Linux). 

Why do you want to use 8.04 or 8.10 anyway?

---

### Post by Earl-Grey on 2012-03-07
Thanks for the advice. I will try to get it to work with Wubi.

Ubuntu 8 has support for my Ati 200m GPU when new version doest have the correct drivers and Ubuntu runs a little slow :)

---

### Post by 3Miro on 2012-03-07
> **Earl-Grey said:**
> Thanks for the advice. I will try to get it to work with Wubi.

Ubuntu 8 has support for my Ati 200m GPU when new version doest have the correct drivers and Ubuntu runs a little slow :)

Is it the default driver or a proprietary driver? You cannot install proprietary drivers (or in fact any additional software) on Ubuntu 8.04 and 8.10. The servers containing the software are off-line.

On 8.04 or 8.10, you can run the default set of installed programs: some old version of Firefox, some basic games, old version of Open Office and couple of chat clients. You cannot install additional media codecs nor browsers nor any other useful programs including proprietary drivers.

You can try to install programs manually by compiling, but you will be missing compilers and important libraries and it will probably be more than what you would want to deal with.

Doesn't Ubuntu 10.04 support your video card?

---

### Post by Earl-Grey on 2012-03-07
Ubuntu 11 supports my graphics card, but it is a little slow. I have used Ubuntu 8 before and it was pretty smooth. I could also get the compiz effects to work and the cube :D

In Ubuntu 11, I have a typing delay of about 3 seconds and click delay. As my computer is pretty old I think that Ubuntu 8 is the best.

I think that the Ati 200m is only supported on Ubuntu 8 and not after.

---

### Post by mastablasta on 2012-03-07
try xubuntu. and try the latest version that uses the latest opensource drivers.

yes no more proprietary drivers for that card. but opensource are gettign better though i am not sure where they are on your chip.

according to this tabel here it should have good 3D support:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
> 
RS400/RS480                 Radeon XPRESS 200(M)/1100 IGP

---

### Post by 3Miro on 2012-03-07
> **Earl-Grey said:**
> Ubuntu 11 supports my graphics card, but it is a little slow. I have used Ubuntu 8 before and it was pretty smooth. I could also get the compiz effects to work and the cube :D

In Ubuntu 11, I have a typing delay of about 3 seconds and click delay. As my computer is pretty old I think that Ubuntu 8 is the best.

I think that the Ati 200m is only supported on Ubuntu 8 and not after.

Earl-Grey, please note that there is no Ubuntu 11 or Ubuntu 8. There are 8.04, 8.10, 9.04 ... 11.04 and 11.10. Those correspond to months and years, i.e. 8.04 is April 2008 and 11.10 is October 2011. You can say 8.* or 8.xx to indicate both 8.04 and 8.10, but saying Ubuntu 8 is incorrect. This can be especially problematic for Ubuntu 11.04 vs 11.10 as they are using different versions of Gnome and people may be confused as to how to help you.

I can understand your frustration about the ATI drivers, but this has nothing to do with Ubuntu and unfortunately going back to a dead distribution from 4 years ago will not work. You will not be able to install the proprietary driver the regular way and even if you find the manual installer in some corner of the web, you will not have any decent applications available.

A much more viable solution would be to try a different desktop environment. From your current install of Ubuntu 11.10 (I am assuming it is 11.10), you can install both XFCE and LXDE. They are both slimmer and snappier than Gnome. XFCE has almost as many features as Gnome and XFCE is my DE of choice even on powerful computers, however, I find LXDE to work much better on machines with weak graphics. Check the Psychocats tutorial on how to install and remove different desktop environments under Ubuntu (make sure you look for the instruction for your specific version).

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

