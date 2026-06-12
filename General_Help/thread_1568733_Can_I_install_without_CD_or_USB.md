---
title: "Can I install without CD or USB??"
date: 2010-09-05
forum: General Help
---

### Post by arashiko28 on 2010-09-05
I got a Dell Optiplex GX150, kinda old, Pentium III, 512 MB RAM, but working, except on the fact that don't recognize any DVD rom, DVD burner I have... the bios boot order shows: CD-ROM (not installed). I have checked the cables, jumpers, and nothing, but the device does open and receives the CD, and the light flashes...

On the other hand, I checked for the possibilities of installing with USB, but can't do it, don't have the option... what do I do now?

The computer has Lubuntu installed, because it was already on the hard drive.

---

### Post by cj.surrusco on 2010-09-05
I'm thinking that your last option would be a PXE boot, which would cause a whole lot more headaches than just buying/borrowing a USB CD-ROM drive, unless you already have a PXE server set up ;).

---

### Post by arashiko28 on 2010-09-05
No, I don't, in fact, I don't even know what that is... but the problem seems to be that don't recognize any drive that I install...

---

### Post by cj.surrusco on 2010-09-05
Actually, Grub 2 supports booting an .iso that's stored on a hard drive. You might want to check that out, I've never done it before.

Here's a link that I found:
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Loopback_Boot_Entry](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Loopback_Boot_Entry)

---

### Post by mike555 on 2010-09-05
In your case you might want to take the harddrive out and hook up to another computer to install the operating system .....or onto a USB adapter cord..

---

### Post by arashiko28 on 2010-09-05
JAJAJA!!! I thought it was chinese! I guess that taking the HDD out is easier than trying to deal with GRUB2... Kind of afraid to do more damage than the one can fix... Thanks, I'll see if it works.

---

### Post by arashiko28 on 2010-09-11
I did more damage than apparently the one I can fix... I took the HDD out and placed it on a case and made the installation, but now, the screen just stays black with one (_) blinking... and that's all... so what do I do now? I have tried now 3 different CD/DVD devices and none gets recognized, not even the one that used to work until it what seems to be the day it was pulled out.

---

### Post by bodhi.zazen on 2010-09-11
wubi might be perfect for you.

You could try something like this :

[http://www.ehow.com/how_6110745_install-iso-image-hard-disk.html](http://www.ehow.com/how_6110745_install-iso-image-hard-disk.html)

---

### Post by arashiko28 on 2010-09-12
All that would be great if I could boot... As I said before, now all I have is a _ blinking and nothing more, to add difficulty, it does not recognize any of the 3 DVD I have plugged, I even changed the IDE cable and yet nothing, BIOS shows: CD/DVD drive (not installed), even though is at least receiving power, because it does open and the led blinks...

I will try again today, installing the hard drive on another case and then pray for it to work this way[-o<

---

### Post by Lukas666 on 2010-09-12
> **mike555 said:**
> In your case you might want to take the harddrive out and hook up to another computer to install the operating system .....or onto a USB adapter cord..

And would you expect it to work? When installed on a different hardware?

---

### Post by cj.surrusco on 2010-09-12
> **Lukas666 said:**
> And would you expect it to work? When installed on a different hardware?

It didn't work when I tried it with Windows, I've done it before with Ubuntu. I guess it also depends on how different the hardware is.

---

### Post by arashiko28 on 2010-09-12
Why not? I have done it before... back then the only problem was the video and all I had to do was change it on XORG...
But no, this time it didn't worked...

---

### Post by Lukas666 on 2010-09-12
> **cj.surrusco said:**
> It didn't work when I tried it with Windows, I've done it before with Ubuntu. I guess it also depends on how different the hardware is.

I stand corrected!

---

### Post by arashiko28 on 2010-09-12
Ok... so now let's look for a solution, please! I'm moving out of my parents house and so far they use my laptop, so I want to leave them a working computer for when I'm gone.

---

### Post by Lukas666 on 2010-09-12
> **arashiko28 said:**
> Ok... so now let's look for a solution, please! I'm moving out of my parents house and so far they use my laptop, so I want to leave them a working computer for when I'm gone.

I am confused. It's an older laptop, and you say it has no CD drive but has a DVD drive?

---

### Post by arashiko28 on 2010-09-12
Nop! My laptop is new, the computer is an older desktop that has problems recognizing the Disk drive connected, whether is DVD or CD, it's the same... I took the desktop's hard drive and connected it via USB and made the install, then took it back to the desktop's case and now I have a blinking under scroll and nothing more, it does not boot.

---

### Post by Lukas666 on 2010-09-12
> **arashiko28 said:**
> Nop! My laptop is new, the computer is an older desktop that has problems recognizing the Disk drive connected, whether is DVD or CD, it's the same... I took the desktop's hard drive and connected it via USB and made the install, then took it back to the desktop's case and now I have a blinking under scroll and nothing more, it does not boot.

OK, is there any windows running on the desktop? Hmmm I guess not (or not anymore). Can the drive (in the desktop) read factory burned disks (not home made)?

---

### Post by davidmohammed on 2010-09-12
do you get a grub displayed when you boot?  Press shift during the boot sequence.  If you do, then edit the current kernel and add one of the following boot options after the line containing "quiet splash"

nomodeset
i915.modeset=1
i915.modeset=0

also try removing "quiet splash" and booting - do you see where the text output stops?

---

### Post by arashiko28 on 2010-09-12
There were never a Windows installation on that desktop, and no, it can not read any disk at all because the BIOS shows a not installed message for a disk device.

No I do not see any GRUB message, just a blinking under scroll and I have left it for more than 30 minutes, and nothing...

---

### Post by davidmohammed on 2010-09-12
If you BIOS says no disk device then your HDD isnt plugged in correctly - either faulty cable or faulty HDD - maybe you havent set the master-slave switch correctly.

When you get the BIOS to recognise your HDD, then you'll make some progress with your O/S install.

---

### Post by arashiko28 on 2010-09-12
Hard drive has always been seen, it's the DVD... but now that we came to that, I did some changes, and now the HDD isn't seen and the DVD does... I'm playing with the jumpers now, to see where it does, DVD it's as slave, HDD is as master with slave, HDD not seen, DVD as slave, HDD as cable select, DVD not seen...

---

### Post by coolness on 2010-09-12
When you had a working OS, you could have plugged in a Ubuntu live USB stick while running the OS.

But i guess that option is'nt possible anymore ^^

So, you should either buy a new USB CD reader, and use that to install, or something.

---

### Post by arashiko28 on 2010-09-12
If booting from USB ever was possible, it would have been my first choice, but these models of DELL (Optiplex GS150) do not boot from USB not even with the latest update of BIOS. Also, I could have connected my external DVD from the USB and boot but then again, it's not a choice if the BIOS does not boot from USB.

---

### Post by Lukas666 on 2010-09-12
> **arashiko28 said:**
> Hard drive has always been seen, it's the DVD... but now that we came to that, I did some changes, and now the HDD isn't seen and the DVD does... I'm playing with the jumpers now, to see where it does, DVD it's as slave, HDD is as master with slave, HDD not seen, DVD as slave, HDD as cable select, DVD not seen...

Connect them to two separate controllers, both as Master.

---

### Post by arashiko28 on 2010-09-12
> **Lukas666 said:**
> Connect them to two separate controllers, both as Master.

They were is two separate controllers from the beginning...

There is a conflict that is sure, but i'm running out of options...

---

### Post by Lukas666 on 2010-09-12
> **arashiko28 said:**
> They were is two separate controllers from the beginning...

Then changing option on one should not affect the other. You reported something different (playing with one made the other stop working)

---

### Post by Lukas666 on 2010-09-12
> **arashiko28 said:**
> 
There is a conflict that is sure, but i'm running out of options...

You're not. You just need to report more thoroughly what you're doing.

List the settings when: 

a) HDD works
b) DVD works

---

### Post by Lukas666 on 2010-09-12
> **arashiko28 said:**
> Why not? I have done it before... back then the only problem was the video and all I had to do was change it on XORG...
But no, this time it didn't worked...

Did you try 32bit Ubuntu?

---

### Post by arashiko28 on 2010-09-12
Actually that's what happens, playing with one does bring down the other. Right now is: HDD; cable select and DVD; slave.

And I had to change the HDD because my uncle insists that the capacity it's too much for it... So I changed it to a 40GB drive and played with the jumpers for a while and the above described configuration, and it seems to be running.

---

### Post by Lukas666 on 2010-09-12
> **arashiko28 said:**
> Actually that's what happens, playing with one does bring down the other. Right now is: HDD; cable select and DVD; slave.

And I had to change the HDD because my uncle insists that the capacity it's too much for it... So I changed it to a 40GB drive and played with the jumpers for a while and the above described configuration, and it seems to be running.

So problem solved?

---

### Post by arashiko28 on 2010-09-12
Not yet, still testing...

---

### Post by arashiko28 on 2010-09-12
OK, it's working, but kind of half way, it shows an error message about Primary IDE not found and Secondary IDE not found, and I have to press F1 to boot, otherwise, does nothing, but it's a progress, right?

---

### Post by Sir John on 2010-09-12
Google Wubi it installs you OS side by side so when you boot up you will be able to select which OS you want to boot into.

---

### Post by Lukas666 on 2010-09-12
> **arashiko28 said:**
> OK, it's working, but kind of half way, it shows an error message about Primary IDE not found and Secondary IDE not found, and I have to press F1 to boot, otherwise, does nothing, but it's a progress, right?

Is primary IDE HDD and secondary IDE DVD?

---

### Post by Lukas666 on 2010-09-12
> **arashiko28 said:**
> OK, it's working, but kind of half way, it shows an error message about Primary IDE not found and Secondary IDE not found, and I have to press F1 to boot, otherwise, does nothing, but it's a progress, right?

Also go into BIOS and run IDE autodetection. Are drives set as auto?

---

### Post by arashiko28 on 2010-09-12
Hahaha, thanks, but no, once proved it works, Ubuntu goes in. My dad don't want to deal with virus and antivirus again.

---

### Post by Lukas666 on 2010-09-12
> **arashiko28 said:**
> Hahaha, thanks, but no, once proved it works, Ubuntu goes in. My dad don't want to deal with virus and antivirus again.

are you talking to me? :)

---

### Post by arashiko28 on 2010-09-12
> **Lukas666 said:**
> are you talking to me? :)

No, that was about the double boot.

About what you said, I'm still trying to solve that, it's slow to start and still have to press F1 to boot, the cables are separated and both IDE, now I'll try again with the jumpers.

---

### Post by Lukas666 on 2010-09-12
> **arashiko28 said:**
> No, that was about the double boot.

About what you said, I'm still trying to solve that, it's slow to start and still have to press F1 to boot, the cables are separated and both IDE, now I'll try again with the jumpers.

Leave the jumpers and check the BIOS settings!

---

### Post by arashiko28 on 2010-09-12
BIOS is all AUTO

---

### Post by arashiko28 on 2010-09-12
Well, setting aside the fact that I still have to press F1 to boot, it's working and ready to go. I'll start the installation now, so wish me luck!

---

### Post by arashiko28 on 2010-09-12
All went well, just the F1 issue remaining and an error message before booting:

error: no suitable mode found
error: unknown command "Terminal"

And gnome bars don't show, only the wallpaper, nothing else.

---

### Post by bodhi.zazen on 2010-09-12
> **arashiko28 said:**
> All went well, just the F1 issue remaining and an error message before booting:

error: no suitable mode found
error: unknown command "Terminal"

And gnome bars don't show, only the wallpaper, nothing else.

Could be a bad burn, check the media and md5sum of the iso.

---

### Post by arashiko28 on 2010-09-12
> **bodhi.zazen said:**
> Could be a bad burn, check the media and md5sum of the iso.

Doubt that, since it's the original CD... but I will...

By the way, I'm looking to make Ubuntu lighter, trying to configure openbox to be the default window manager.

PS: I'm on the oldie Pentium III, running well, but a bit slow. I know XFCE should have been my choice, but I forgot to download the .iso.

---

