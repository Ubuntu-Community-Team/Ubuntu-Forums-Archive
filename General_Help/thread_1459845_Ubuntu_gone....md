---
title: "Ubuntu gone..."
date: 2010-04-22
forum: General Help
---

### Post by devildoc5 on 2010-04-22
Ok so here is the basic problem I am running into.  ubuntu partition = GONE

boot from cd = Set in Bios but wont work for some reason!
boot from usb = Set in Bios but wont work ofr some reason!

the MBR is apparently still intact as it says "GRUB recovery>"  but I cannot do anything.  Comp will not bootfrom usb or cd, even after selecting them in the Bios.  I am at a complete and utter loss as to what to do here...Anyone got an idea or two?

BTW this is a Laptop, and the only one I have so no swapping hdd's or anything....

---

### Post by carl4926 on 2010-04-22
Power off the machine.
Remove the battery.

Replace the battery, try again. (A stab in the dark)

---

### Post by r_s on 2010-04-22
you can try and boot from the grub command prompt,  [http://ubuntuforums.org/showthread.php?t=1404540](http://ubuntuforums.org/showthread.php?t=1404540)

---

### Post by devildoc5 on 2010-04-22
I have tried both of the previous mentioned posts.  The linux partition is COMPLETELY gone.  However I have managed to disassemble the connector interface on the laptop hdd and it appears to be SATA underneath...

Gonna try and fire it up in the desktop and see if I cant do something with it that way....

---

### Post by uRock on 2010-04-22
Go to the menu all the way to the right in the BIOS and there should be an offering to restore defaults, use it. All of the USB options should be working on the next attempt.

---

### Post by devildoc5 on 2010-04-22
I have done the restore to defaults option a few dozen times now and it does not seem to work, either.

I have managed to connect the boot drive of the laptop to my desktop as a 3rd drive.  How would I go about changing the MBR so it'll boot the valid version of vista I ahve installed on this hdd?

---

### Post by devildoc5 on 2010-04-22
ok so what I did is reinstall ubuntu to the drive from my sektop, the problem is that I still cannot boot from either the usb or the cd, cd not recognized in either os (two different ones), hp thinks I am gonna send them my laptop along with 300$ so they can reformat everything and give me a different one....

---

### Post by Doug11 on 2010-04-22
Have you tried to use a different cd. I'm also assuming you are using the same image to try boot with off the usb. Or will it boot from your desktop.

---

### Post by devildoc5 on 2010-04-22
I have tried booting with ubuntu 9.10 and 8.10, Slax, puppy, windows 7, vista cd/dvds.  I have tried ubuntu 9.10 and 8.10 on the usb.  I have tried two different cd drives and nothing seems to be working.

---

### Post by carl4926 on 2010-04-22
It's extremely unlikely that both the CD drive and USB booting would fail.
I'm wondering if something more terminal might be the issue.

You could try power off, battery out and battery out of Mobo
Check online for details on re-setting BIOS back to factory default.

---

### Post by devildoc5 on 2010-04-22
I have pulled the CMOS battery and I followed hps steps for doing a "hard reset" something with the power removed and holding down the power button for 30secs.  I have not been able to locate how to jump the cmos though.  not sure if that is even doable in a laptop.  I am glad to see that I am not the only one who's mind has bee boggled by this weird error.

---

### Post by carl4926 on 2010-04-22
> **devildoc5 said:**
> I have pulled the CMOS battery and I followed hps steps for doing a "hard reset" something with the power removed and holding down the power button for 30secs.  I have not been able to locate how to jump the cmos though.  not sure if that is even doable in a laptop.  I am glad to see that I am not the only one who's mind has bee boggled by this weird error.

Since you marked as Solved. Are we to assume it is working?:)

---

### Post by devildoc5 on 2010-04-22
it is "solved" to the point that I can actually boot up into an os.  However I still have no CD support what so ever in either ubuntu or vista.  I also have not boot support except for the notebook hdd....

---

