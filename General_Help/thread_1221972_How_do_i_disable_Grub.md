---
title: "How do i disable Grub?"
date: 2009-07-24
forum: General Help
---

### Post by Psycho.mario on 2009-07-24
Hi, I have installed my GRUB loader onto a floppy using these instructions:
[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)
How can i disable the GRUB loader, so that i need the floppy to boot? At the moment, i can boot from the floppy and get my GRUB loader, or boot from the HDD to get the GRUB loader. Would just renaming the /boot/grub directory work?

Thanks

---

### Post by Krupski on 2009-07-24
> **Psycho.mario said:**
> Hi, I have installed my GRUB loader onto a floppy using these instructions:
[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)
How can i disable the GRUB loader, so that i need the floppy to boot? At the moment, i can boot from the floppy and get my GRUB loader, or boot from the HDD to get the GRUB loader. Would just renaming the /boot/grub directory work?

Thanks

Are you using the floppy as a "key" so that others can't boot up your computer?

Don't remove any files or directories... because the boot files you need COME from "/boot".

If you want to make the hard drive version of GRUB fail to work, simply "get rid" of the file "menu.lst"...

Do this:

```

sudo mv /boot/grub/menu.lst /boot/grub/disabled.menu.lst

```

By renaming menu.lst, the hard drive GRUB will fail. And, if you ever want to put it back, just rename the file back to normal.

Note that if your boot floppy gets messed up, your only way "back in" would be to boot up a live CD and then rename the "disabled.menu.lst" file back to normal.

I would suggest that you either have a few spare boot floppies, or instead make a boot USB stick.

Buy a cheap 1 gig or smaller (the smallest, cheapest one you can buy is more than enough).

Then, just setup the USB stick as your "boot key".

Lastly, remember that if you do any updates, some of them (like a kernel update) will want to build a new "initrd.img" and update Grub's "menu.lst" file. Your floppy disk will need to be in the drive to be updated... and you'll have to check to be sure that indeed the FLOPPY was updated rather than a new "menu.lst" created on the hard drive.

Hope this helps...

-- Roger

---

### Post by BartowBiggz on 2009-07-24
Now just to make sure I got this right...this WILL work in the case of me trying to repair my vista's MBR right?. The issue i have ben having with my dual booted laptop is that I cannot boot into vista anymore i get the option to choose which OS i want to boot but when i choose vista it gives me the options to start normally or repair it when i choose the repair it just blinks back to the original screen with the latter opitions when I press F8 none of the repair options work cannot even boot it up in safe mode all of the so called "fixes" for the issue all are centered around repairing from the vista cd...(which i know your thinking this has nothing to do with the original question lol)which the machine will not boot from even after changing the order in the bios and from the boot order splash screen. I think that the GRUB is the culprit so pretty much what i was wondering was will this after i execute it therefore enable the laptop to boot from cd?Sorry so long fingered....(and BTW the CD-ROM does work)

---

### Post by Psycho.mario on 2009-07-24
I have the floppy with GRUB on it, two identical backup copies, and an image which i could write to a floppy on my other computer if the need arises. Will renaming the menu.lst give me an error? I would rather have it so there was no error at all. I will try it and re-post when i have seen the effects. If this is successful, i'll write a script to check for changes in the menu.lst file, so i can update the flopy when the need arises. 

Thanks

---

### Post by unutbu on 2009-07-24
Here are 2 alternatives to Krupski's method:
[list]
[*]Boot Ubuntu. Edit /boot/grub/menu.lst. (Copy it back to /boot/grub/menu.lst if you have moved it.)

Go down about 2/3 of the way through the file.
Remove all boot stanzas from the file.

A boot stanza looks something like this:```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		1f57f1e1-a3a8-4b83-998f-36bfeed2d3c9
kernel		/vmlinuz-2.6.27-11-generic root=/dev/mapper/vg_intrepid-OS3 ro quiet 
initrd		/initrd.img-2.6.27-11-generic
quiet
```

Insert the following boot stanza:
```

title Insert boot floppy
device (fd0) /dev/fd0
root (fd0)
chainloader +1
```
By doing this, when you boot from the hard drive, you will get to a GRUB menu with only one option: "Insert boot floppy". When you select this option, GRUB will start reading the floppy drive for a boot loader.

I haven't tested this, but I think it should work.

[*] Or you could just wipe the MBR off the hard drive:
```

sudo dd if=/dev/zero of=/dev/sdX bs=446 count=1
```

This command writes zeros to the MBR on sdX (bytes 1--446) without touching the partition table (bytes 447--512). Change sdX to the appropriade device name for your hard drive.

If you zero the MBR, and try to boot of the hard drive, you will get a GRUB boot error. 
[/list]

---

### Post by Krupski on 2009-07-24
> **BartowBiggz said:**
> Now just to make sure I got this right...this WILL work in the case of me trying to repair my vista's MBR right?.

Let's see if I understand what's going on here... I ASSUME:

You installed Vista, and it booted fine.

You then installed Linux and installed GRUB on the MBR (Master Boot Record).

At bootup, you could choose between Linux or Windows from a GRUB menu.

Along the way, something happened to the Linux install (changed, updated, deleted)?

Now, you can't boot Windows anymore.

IF this is right, what you have to do is RE-INSTALL the MBR of Vista.

I use XP, not Vista, but I suspect the procedure is the same.

Try this:

Boot up Vista from the Vista DVD. Choose "Repair this installation by using the recovery console".

In the recovery console (a DOS-like black screen with white text), type these two commands:

```

fixboot
fixmbr

```

When you're done, type "exit" and remove the Vista DVD.

Vista should now boot up normally (although you won't have any access to Linux anymore... except by booting a live CD).

If you want to get back into dual booting, search the web for how to setup dual Windows/Linux boot by using "NTLDR" instead of Grub.

Good luck... hope this helps.

-- Roger

---

### Post by Krupski on 2009-07-24
> **unutbu said:**
> [COLOR="Red"][B][*] Or you could just wipe the MBR off the hard drive:

sudo dd if=/dev/zero of=/dev/sdX bs=446 count=1[/B][/COLOR]

This command writes zeros to the MBR on sdX (bytes 1--446) without touching the partition table (byts 447--512). Change sdX to the appropriade device name for your hard drive.

If you zero the MBR, and try to boot of the hard drive, you will get a GRUB boot error. 
[/list]

I highlighted part of your quote in red... you should clearly warn the user that this is a potentially dangerous command and they should not do it unless they know EXACTLY what will happen and how to fix the MBR from that point on.

-- Roger

---

### Post by Psycho.mario on 2009-07-24
I don't want to get rid of the MBR, just in case. I'll try editing the menu.lst file, see if that works.

Thanks

---

### Post by BartowBiggz on 2009-07-25
Thanks for taking the time out to answer my post but as i mentioned in the latter part of the post that i am unable to boot from the cd so im still stuck at square one...

---

### Post by Psycho.mario on 2009-07-25
Ok, i added:
```
default 0
timeout 3
hiddenmenu
title   Reboot
reboot

```
as my only entry in menu.lst, so it reboots in a loop until the floppy is inserted.

Thanks for your help

---

