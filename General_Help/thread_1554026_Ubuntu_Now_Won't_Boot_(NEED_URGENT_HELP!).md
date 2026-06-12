---
title: "Ubuntu Now Won't Boot (NEED URGENT HELP!)"
date: 2010-08-16
forum: General Help
---

### Post by Jakiejake on 2010-08-16
Hi,
The other day I was doing some hardware on my computer was on
It then mysteriously shut off everything on my surge board (Monitor, Speakers and Computer)
I then turned everything back on but then had no sound
So I decided to restart only to find out that I see my Motherboard boot screen (Gigabyte) and then my CMOS go off
Once it gets to the part where it goes to load Ubuntu I get a flashing _ for about 2 seconds then my monitor goes to sleep with the reason "No Signal!"
I don't hear the Ubuntu African Drums sound or anything else
I have managed to boot into my Linux Mint 8 Live CD and got sound from that but I still can't get into Ubuntu
I'm using Ubuntu 10.04 Lucid Lynx 64 Bit and I'm pretty sure I have all the updates installed
Oh and I have auto login enabled
I really need help as I need/want to use my computer ASAP!
Thanks
-Jacob

---

### Post by Jakiejake on 2010-08-16
Please help!

---

### Post by lisati on 2010-08-16
> **Jakiejake said:**
> Please help!

Please be patient. We are all volunteers here. The person best able to help you might not have seen your question yet.

---

### Post by Jakiejake on 2010-08-16
> **lisati said:**
> Please be patient. We are all volunteers here. The person best able to help you might not have seen your question yet.

Why couldn't you try and help me
I'm running of a Linux Mint 8 Live CD here!!!

---

### Post by prshah on 2010-08-16
> **Jakiejake said:**
> goes to load Ubuntu I get a flashing _ for about 2 seconds then my monitor goes to sleep with the reason "No Signal!"

a) The "No signal" part usually indicates that when switching to graphics mode, the refresh rate is out of the range of the monitor, so I doubt it's indicative of any problems.

b) If the last run has been interrupted, Ubuntu will first try to run a check of the HDD(s). This may be the reason why you are not getting the login sound. 

c) You can check if the HDD check is running by looking at the HDD activity LED. If it is burning (solid, or blinking) then probably the check is running. In this case, please wait a while (7~10 mins should be enough), and your desktop may appear.

d) If it does not appear, or if you cannot wait, please try to boot into recovery mode. If you can boot into recovery mode, please give the (root) terminal commands ```
touch /forcefsck
reboot
``` This should reboot and trigger an automatic HDD check.

e) If none of these suggestions work (please exercise patience), then please post back for further suggestions to check if there is some other problem.

---

### Post by diablo75 on 2010-08-16
> **Jakiejake said:**
> Hi,
The other day I was doing some hardware on my computer was on
It then mysteriously shut off everything on my surge board (Monitor, Speakers and Computer)

What EXACTLY were you doing?

---

### Post by Sef on 2010-08-16
What graphics card do you have?

---

### Post by Jakiejake on 2010-08-16
> **prshah said:**
> a) The "No signal" part usually indicates that when switching to graphics mode, the refresh rate is out of the range of the monitor, so I doubt it's indicative of any problems.

b) If the last run has been interrupted, Ubuntu will first try to run a check of the HDD(s). This may be the reason why you are not getting the login sound. 

c) You can check if the HDD check is running by looking at the HDD activity LED. If it is burning (solid, or blinking) then probably the check is running. In this case, please wait a while (7~10 mins should be enough), and your desktop may appear.

d) If it does not appear, or if you cannot wait, please try to boot into recovery mode. If you can boot into recovery mode, please give the (root) terminal commands ```
touch /forcefsck
reboot
``` This should reboot and trigger an automatic HDD check.

e) If none of these suggestions work (please exercise patience), then please post back for further suggestions to check if there is some other problem.

How do I boot into recovery mode
I'll google it but please post it here

---

### Post by lisati on 2010-08-16
> **Jakiejake said:**
> Why couldn't you try and help me
I'm running of a Linux Mint 8 Live CD here!!!

Simple answer: I don't use Linux Mint.

---

### Post by Jakiejake on 2010-08-16
> **diablo75 said:**
> What EXACTLY were you doing?

Using a TiP31c Transistor to control lights to music
I was using the Molex connector with bare wires since I didn't have a connector in reach and accidently touched the wire to the wrong part and I think I overloaded the surge board causing it to reset!

---

### Post by Jakiejake on 2010-08-16
> **lisati said:**
> Simple answer: I don't use Linux Mint.

I don't anymore either
I use Ubuntu but I'm using my Mint CD (For some reason the Ubuntu Live CD won't boot and Mint comes with Flash on the CD)

---

### Post by Jakiejake on 2010-08-16
> **sef said:**
> what graphics card do you have?

ati

---

### Post by Jakiejake on 2010-08-16
> **Jakiejake said:**
> How do I boot into recovery mode
I'll google it but please post it here

Okay I've found out you have to hold down Shift while (I single boot) but when I do my system just restarts it's self!
What do I do :confused:

---

### Post by Jakiejake on 2010-08-16
Anyone Know?

---

### Post by Jakiejake on 2010-08-16
> **Jakiejake said:**
> Anyone Know?

:confused:

---

### Post by diablo75 on 2010-08-16
> **Jakiejake said:**
> Using a TiP31c Transistor to control lights to music
I was using the Molex connector with bare wires since I didn't have a connector in reach and accidently touched the wire to the wrong part and I think I overloaded the surge board causing it to reset!

It's quite possible you seriously damaged your power supply, to the point where it's just producing enough power to get the computer to work but it's walking on the edge of a knife.  Video cards suck a lot of juice which might explain why when it goes into another video mode the computer locks up or reboots due to an increase in energy usage.  It's just a theory.

In short, I really think you'd be wasting time hunting out a software glitch when you just shorted your power supply out while the computer was running.  It is MUCH more likely you have a hardware problem on your hands.

---

### Post by Jakiejake on 2010-08-16
> **diablo75 said:**
> It's quite possible you seriously damaged your power supply, to the point where it's just producing enough power to get the computer to work but it's walking on the edge of a knife.  Video cards suck a lot of juice which might explain why when it goes into another video mode the computer locks up or reboots due to an increase in energy usage.  It's just a theory.

In short, I really think you'd be wasting time hunting out a software glitch when you just shorted your power supply out while the computer was running.  It is MUCH more likely you have a hardware problem on your hands.

Then Why Can I run Linux Mint 8 off a live CD?
I really don't want to go out and spend $100 bucks on a good quality power supply!

---

### Post by Jakiejake on 2010-08-16
> **diablo75 said:**
> It's quite possible you seriously damaged your power supply, to the point where it's just producing enough power to get the computer to work but it's walking on the edge of a knife.  Video cards suck a lot of juice which might explain why when it goes into another video mode the computer locks up or reboots due to an increase in energy usage.  It's just a theory.

In short, I really think you'd be wasting time hunting out a software glitch when you just shorted your power supply out while the computer was running.  It is MUCH more likely you have a hardware problem on your hands.

Oh and why could I boot into Ubuntu after I did what I did but not after I rebooted again?

---

### Post by Jakiejake on 2010-08-16
I might try and borrow the monitor from downstairs when I get time

---

### Post by diablo75 on 2010-08-16
> **Jakiejake said:**
> Then Why Can I run Linux Mint 8 off a live CD?
I really don't want to go out and spend $100 bucks on a good quality power supply!

Well something you might try to do is reset your BIOS to the factory defaults.  There is at least one way to do this; possibly two.

You should consult your motherboards documentation but typically there is a jumper on a bank of three pins, with the jumper connecting two pins.  Like this:

[x x] x

And you want to move this jumper to the reset position, like this:

x [x x]

If you don't want to hunt for jumpers, another way to reset your BIOS is to:

1.  Remove the power cord from the PC.
2.  Find the little battery that looks like this and remove it from the board for 2 minutes:

[IMG]http://laptopsgate.com/wp-content/uploads/2010/04/cmos-battery-on-gateway-m-6823-laptop.gif[/IMG]

Then put it back in, plug the power cord in, and turn the PC on to see what happens.

If this doesn't solve the problem, one possible explanation for your system failing is due to some bizarre corruption on your hard drive sustained as a result of an abrupt spike in power.  It would make sense for a Live CD to work because it doesn't depend on the hard drive to work at all.  If the hard drive was only logically damaged, you could try to format it and re-install.  But if it was physical damage... you're screwed. 

Before doing that you might try to access the drive using the Mint Live CD to access anything you can't afford to lose.  If you're having problems with the Ubuntu Live CD, have you tried the Alternative (text-based) CD instead?

---

### Post by Jakiejake on 2010-08-16
OMG OMG OMG OMG OMG OMG
I JUST PLUGGED IN THE OTHER MONITOR AND IT WORKED!
I'll enjoy my computer for now and try to fix the problem with the other monitor now!

---

### Post by Gustav521 on 2010-08-16
I hope someone can help with this problem. I tried to upgrade Grub .97 to Grub2 1.96. Now all I get is black screen with "Grub>" prompt. Looks like the installation did not go well. What do I do to again have access to my 9.04 jaunty system?? Thank you.

---

### Post by Nick_Jinn on 2010-08-16
The problem might be that the latest version of Ubuntu might not support certain video cards that earlier versions do support....Its strange, but something obviously make some hardware support no longer backwards compatible.

---

