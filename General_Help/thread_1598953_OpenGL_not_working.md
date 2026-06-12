---
title: "OpenGL not working"
date: 2010-10-17
forum: General Help
---

### Post by Bv202 on 2010-10-17
Hey,

OpenGL is not working on my installation. I'm completely new to Linux and have been trying to get it to work for hours, but whatever I try, it just doesn't work.

When I try to load java applets which use OpenGL, the applet crashes with this error:
> #
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb7895424, pid=3239, tid=1586695024
#
# JRE version: 6.0_22-b04
# Java VM: Java HotSpot(TM) Server VM (17.1-b03 mixed mode linux-x86 )
# Problematic frame:
# C  [+0x424]  __kernel_vsyscall+0x10
#
# An error report file with more information is saved as:
# /home/bjorn/Bureaublad/hs_err_pid3239.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Afgebroken


I first thought it was related to Java, but it seems it isn't. I've been reading information about video card drivers in Linux for hours, but I'm really stuck...

I currently got the drivers Ubuntu offered me installed (fglrx).
If I remove these via synaptic, the applet does NOT crash anymore but on the next reboot Ubuntu won't start anymore (black screen) and I have to use the recovery mode to install fglrx again.

If I remove fglrx via the extra drivers menu in Ubuntu, my system still boots but the drivers are removed so no more OpenGL.

The strange this is: if I remove fgrlx via syntaptic and don't restart my computer, the applet doesn't crash anymore so it's really related to these drivers.

I'm really stuck what to do now. I've tried to install "open source" drivers, but I failed with that. I really don't understand how to correctly install them. I've tried several fixes for OpenGL crashes, but none of them works.

My GPU is: ATI Radeon HD5470

If you need any information, please also explain me how to get it as I'm a noob in Linux.

Thanks

---

### Post by sendblink23 on 2010-10-17
> **Bv202 said:**
> Hey,

OpenGL is not working on my installation. I'm completely new to Linux and have been trying to get it to work for hours, but whatever I try, it just doesn't work.

When I try to load java applets which use OpenGL, the applet crashes with this error:


I first thought it was related to Java, but it seems it isn't. I've been reading information about video card drivers in Linux for hours, but I'm really stuck...

I currently got the drivers Ubuntu offered me installed (fglrx).
If I remove these via synaptic, the applet does NOT crash anymore but on the next reboot Ubuntu won't start anymore (black screen) and I have to use the recovery mode to install fglrx again.

If I remove fglrx via the extra drivers menu in Ubuntu, my system still boots but the drivers are removed so no more OpenGL.

The strange this is: if I remove fgrlx via syntaptic and don't restart my computer, the applet doesn't crash anymore so it's really related to these drivers.

I'm really stuck what to do now. I've tried to install "open source" drivers, but I failed with that. I really don't understand how to correctly install them. I've tried several fixes for OpenGL crashes, but none of them works.

My GPU is: ATI Radeon HD5470

If you need any information, please also explain me how to get it as I'm a noob in Linux.

Thanks

I'm assuming you are using Ubuntu 10.10 right?
Well for me on my 5770's OpenGL works 100% fine.. just look at this screenshot, these games are running on OpenGL at 100% speed:
[[IMG]http://img687.imageshack.us/img687/6167/screenshotebv.th.jpg[/IMG]](http://img687.imageshack.us/img687/6167/screenshotebv.jpg)

As well Photoshop CS5 - its detecting my Video Card & it says OpenGL enabled - zooming & 3D works
[[IMG]http://img219.imageshack.us/img219/5051/screenshot2z.th.jpg[/IMG]](http://img219.imageshack.us/img219/5051/screenshot2z.jpg)

And I simply used the System > Administration > Additional Drivers  = which is the FGLRX

Can you try reinstalling(activating) FGLRX through the regular gnome menu (not synaptics)... reboot and afterwards getting back in the desktop open up Terminal and run: fglrxinfo
To see what version of OpenGL you have...  mines: 4.0.10237

---

### Post by Bv202 on 2010-10-17
Hey,

I think I re-installed the drivers about 5 times already, still doesn't work.

My output:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 5000 Series
OpenGL version string: 4.0.10237 Compatibility Profile Context

But like I said before: If I remove the drivers, but don't restart my computer yet, the applet doesn't crash. So it's really some sort of setting of fglrx.

---

### Post by sendblink23 on 2010-10-17
Can I test the java applet thing you are working on.. to see if it works on my side....  since i can notice you pretty much are running my same driver... I'd assume I will have the same error as yours

so yeah where should I go to test what you are trying to use

---

### Post by Bv202 on 2010-10-17
> **sendblink23 said:**
> Can I test the java applet thing you are working on.. to see if it works on my side....  since i can notice you pretty much are running my same driver... I'd assume I will have the same error as yours

so yeah where should I go to test what you are trying to use

It's not just one applet...it's just any applet which uses OpenGL (even games like RuneScape).

I'm trying to play Minecraft (you need to buy the game before being able to play it). But I've asked others and I'm the only one with this issue.

---

### Post by sendblink23 on 2010-10-17
> **Bv202 said:**
> It's not just one applet...it's just any applet which uses OpenGL (even games like RuneScape).

I'm trying to play Minecraft (you need to buy the game before being able to play it). But I've asked others and I'm the only one with this issue.

Runescape works perfectly fine over here:
[[IMG]http://img294.imageshack.us/img294/9382/screenshot3dd.th.jpg[/IMG]](http://img294.imageshack.us/img294/9382/screenshot3dd.jpg)

so.. yeah something must be very odd on your computer... well I mean laptop

Do you have installed  Restricted Ubuntu... wteee   from Ubuntu Software Center  ?


I'm planning on buying Minecraft.. looks pretty cool so far

---

### Post by Bv202 on 2010-10-17
> Do you have installed Restricted Ubuntu... wteee from Ubuntu Software Center ?
Eeh.. could you explain this a bit?

---

### Post by sendblink23 on 2010-10-17
> **Bv202 said:**
> Eeh.. could you explain this a bit?

open up:

Applications > Ubuntu Software Center

Type in: ubuntu res    

and you will see what I mean  :P install it

Oh I'll suggest you as well inside Ubuntu Software Center   install: Chromium  web browser (just incase, since that is where I'm playing runescape)
Forgot to mention after installing those things.. it might be good to restart the computer to make sure everything you installed gets loaded properlly... then test runscape through Chromium ... hopefully it works...  then try  Minecraft

---

### Post by Bv202 on 2010-10-17
Didn't work :(

It's not browser related as Minecraft isn't run in a browser :)

---

### Post by Bv202 on 2010-10-17
I've removed the Ubuntu partition and installed Ubuntu (for the third time already) again. And guess what... EXACTLY THE SAME PROBLEM.

I'm really getting frustrated by this operating system.

---

### Post by sendblink23 on 2010-10-17
Well conclusion.. its probably because your card is 5xxx series mobile version(its way different than the desktop version)... I don't know if the fglrx driver has any limits compatibility or if they have done any testings on laptops that have your card... :(

Another idea could be testing the actual ATI catalyst driver
But you have to wait for the actual release of Catalyst 10.10 drivers... right now they are still in beta, and the 10.9 drivers that are offered on ati's website is not compatible with Maverick Meerkat 10.10 - Lucid 10.04 does support the cat 10.9 drivers

You may do that, download the previous Ubuntu version.. maybe it will work for you over there... that is if you want to keep testing.. trying things out... something must get it working on your laptop... but if all fails...yeah it might be better to give up & not waste your time on this hassle...

---

