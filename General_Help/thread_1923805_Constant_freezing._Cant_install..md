---
title: "Constant freezing. Cant install."
date: 2012-02-11
forum: General Help
---

### Post by thatguy93 on 2012-02-11
Hey guys,
I'm trying to install Xubuntu 11.10 on my laptop (Acer Aspire One D552) and I am having a slight issue. The operating system ALWAYS freezes. I tried the "default" option on boot up, it loads up, but about 5 mins in everything freezes. I also tried "Install Xubuntu" on boot up, but same thing. I tried redownloading the ISO a few times, but no luck. I'm using a USBdrive to install it. I put the ISO on it with Unetbootin.

I also tried to install xubuntu 11.04, but had some hardware issues. So 11.10 is the only option. Anyone know what the issue is, or how to fix it?

Thanks guys!

---

### Post by frone on 2012-02-11
Have you tried to run the memory test from the installation CD?  Let it run through a full pass to see if you get any errors.  Might not be the cause, but certainly the fastest easiest possible thing to eliminate as the cause...

---

### Post by wolfen69 on 2012-02-11
Run MemTest first before anything else. Btw, nice avatar!

---

### Post by thatguy93 on 2012-02-11
> **frone said:**
> Have you tried to run the memory test from the installation CD?  Let it run through a full pass to see if you get any errors.  Might not be the cause, but certainly the fastest easiest possible thing to eliminate as the cause...

> **wolfen69 said:**
> Run MemTest first before anything else. Btw, nice avatar!

Okay thanks guys, I'll run that now.


Thanks Wolfen. I'm pretty much obsessed with wolves. My username is Wolf on every website I'm on, minus this one of course. Wearing my Swarovski Wolf fang necklace right now haha.

---

### Post by Bucky Ball on 2012-02-11
Have you tried the Alternate CD or setting 'nomodset' or one of the other options by hitting F6 (from memory) at the first screen when booting from CD?

---

### Post by thatguy93 on 2012-02-11
Okay when I try to run the memory test I get:  

> Cannot load a ramdisk with and old kernel image

> **Bucky Ball said:**
> Have you tried the Alternate CD or setting 'nomodset' or one of the other options by hitting F6 (from memory) at the first screen when booting from CD?

I have not tried the alternate CD yet.
Hitting F6 doesnt do anything :/


EDIT:
Installed the .ISO to my flashdrive with a different program (Universal usb installer), so I will try everything out, and update the thread.

---

### Post by thatguy93 on 2012-02-11
Okay so far this is making a huge difference. No freezing issues at all. I'll report back when the install is complete.

EDIT:

Spoke to soon. Just froze up. Going to try in nomodeset


Alright not getting anywhere. "nomodeset" didnt help. Still freezes. Did the memtest, passed, no errors.

---

### Post by LinuxFan999 on 2012-02-11
Have you tried Xubuntu 10.04?

---

### Post by thatguy93 on 2012-02-11
> **LinuxFan999 said:**
> Have you tried Xubuntu 10.04?

Ya, 11.04 does not like my laptop. Lots of issues. I could install 11.04 and then do the upgrade. What do you think?

---

### Post by wolfen69 on 2012-02-11
> **thatguy93 said:**
> Ya, 11.04 does not like my laptop. Lots of issues. I could install 11.04 and then do the upgrade. What do you think?

I myself am not a fan of upgrades, as I prefer fresh installs, but it may be the only way for you right now. Good luck.

---

### Post by thatguy93 on 2012-02-11
> **wolfen69 said:**
> I myself am not a fan of upgrades, as I prefer fresh installs, but it may be the only way for you right now. Good luck.

Ya same here. Everytime I upgrade Ubuntu it screws up. I'm just going to leave it until the next update comes out. Now my laptop is useless, because Win(lose) 7 is gone.

---

### Post by savanna on 2012-02-11
Do a memtest first - fault hardware?

---

### Post by thatguy93 on 2012-02-11
> **savanna said:**
> Do a memtest first - fault hardware?

Already did one. No errors.

---

### Post by Gremlinzzz on 2012-02-11
try a different OS :popcorn:
 [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by thatguy93 on 2012-02-11
> **Gremlinzzz said:**
> try a different OS :popcorn:
 [http://distrowatch.com/](http://distrowatch.com/)

I prefer Ubuntu/Xubuntu, or Fedora(Fedora more, run it on my desktop).

---

### Post by frone on 2012-02-12
Time for some troubleshooting.  Do *everything* diferent and try again.  If you have two memory DIMMs in the laptop, remove one.  On AC power?  Unplug and use the battery.  Anything plugged into USB?  Remove it.  Check for a BIOS upgrade for the laptop (post back the model# if you need help) and apply it.

Do as many things different as you can think of - then attept the installation again - using the alternative install media.

Post back anything different from the previous failures.  Good luck...

---

### Post by thatguy93 on 2012-02-12
> **frone said:**
> Time for some troubleshooting.  Do *everything* diferent and try again.  If you have two memory DIMMs in the laptop, remove one.  On AC power?  Unplug and use the battery.  Anything plugged into USB?  Remove it.  Check for a BIOS upgrade for the laptop (post back the model# if you need help) and apply it.

Do as many things different as you can think of - then attept the installation again - using the alternative install media.

Post back anything different from the previous failures.  Good luck...
So far I have tried everything. I have yet to try the alternate ISO. Guess I'll try that now.

EDIT:
Alternate doesnt work either. I get an error that "Select and Install Software" failed.
I'm going to try Lubuntu, even though I hate the GUI.

---

### Post by Bucky Ball on 2012-02-12
> **thatguy93 said:**
> 
I'm going to try Lubuntu, even though I hate the GUI.

Just install another desktop environment when installed. I use xfce for all my puters. In software centre you install xfce4, log out, choose 'xfce session' from the 'Sessions' pop-up menu, log back in again. No more Lxde DE.

---

### Post by thatguy93 on 2012-02-12
> **Bucky Ball said:**
> Just install another desktop environment when installed. I use xfce for all my puters. In software centre you install xfce4, log out, choose 'xfce session' from the 'Sessions' pop-up menu, log back in again. No more Lxde DE.

Unfortunetely, Lubuntu did not work either, it also froze. Something is either wrong with my USB, or my laptop. However, my laptop worked fine with windows 7, it was just slow (well compared to my PC lol).

---

### Post by Bucky Ball on 2012-02-12
When you try the Linux release from the disk (the install disk choosing option 'Try Ubuntu' or whichever you are using) does it successfully run or it won't run from the LiveCD either?

... and just remind me, you have tried 'nomodset' from the F6 options at that install screen where you see 'Try Xubuntu'? You might try some of the acpi options (acpi=off for instance) also and see if that helps.

---

### Post by thatguy93 on 2012-02-12
> **Bucky Ball said:**
> When you try the Linux release from the disk (the install disk choosing option 'Try Ubuntu' or whichever you are using) does it successfully run or it won't run from the LiveCD either?

... and just remind me, you have tried 'nomodset' from the F6 options at that install screen where you see 'Try Xubuntu'? You might try some of the acpi options (acpi=off for instance) also and see if that helps.

It runs for abit, then freezes.
I have tried "nomodeset" it did not help. As for the others, I didnt try them because I heard some are bad. But I'll try them anyways.

---

### Post by Bucky Ball on 2012-02-13
> **thatguy93 said:**
> As for the others, I didnt try them because I heard some are bad. But I'll try them anyways.

Good plan. Try the acpi options, as I suggested. No damage can happen to the machine, hardware, or install. It will just make some things (hardware things and related software things) work or not work, which can either get the install happening or not.

Maybe someone else can chime in with some other suggestions. I've forced installs with all sorts of options and you can generally sort out what the problem is or/and install appropriate drivers once your installed and running from a Ubuntu (whatever desktop environment) desktop. ;)

---

### Post by LewisTM on 2012-02-13
You should take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1811178"), which is about the Acer 722 but should also apply to the 522 as they are very similar. Also this [Wiki]("https://help.ubuntu.com/community/AspireOne522#Ubuntu_installation") helps.

Basically the culprit is the boot order. In the BIOS you need to set the order to be Network first (and leave the cable unplugged). This allows the network hardware to properly initialize and then crashes are gone. 

Once this is done there are a number of others tricks you can apply to increase performance and decrease power consumption.

I run Xubuntu on a 722 and it is lightning fast, everything runs perfectly.

Cheers!

---

### Post by thatguy93 on 2012-02-13
> **Bucky Ball said:**
> Good plan. Try the acpi options, as I suggested. No damage can happen to the machine, hardware, or install. It will just make some things (hardware things and related software things) work or not work, which can either get the install happening or not.

Maybe someone else can chime in with some other suggestions. I've forced installs with all sorts of options and you can generally sort out what the problem is or/and install appropriate drivers once your installed and running from a Ubuntu (whatever desktop environment) desktop. ;)

Last night I put Xubuntu back on my USB with pendrive, but didnt have any F# options. So I left it till this morning, but Lewis' fix worked!

> **LewisTM said:**
> You should take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1811178"), which is about the Acer 722 but should also apply to the 522 as they are very similar. Also this [Wiki]("https://help.ubuntu.com/community/AspireOne522#Ubuntu_installation") helps.

Basically the culprit is the boot order. In the BIOS you need to set the order to be Network first (and leave the cable unplugged). This allows the network hardware to properly initialize and then crashes are gone. 

Once this is done there are a number of others tricks you can apply to increase performance and decrease power consumption.

I run Xubuntu on a 722 and it is lightning fast, everything runs perfectly.

Cheers!

AHA! Perfect! Thank you very much! Worked like a charm! 

Thanks for all the help guys!

---

