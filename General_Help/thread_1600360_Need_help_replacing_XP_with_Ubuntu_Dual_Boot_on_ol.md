---
title: "Need help replacing XP with Ubuntu Dual Boot on old desktops w/ 2 IDE drives"
date: 2010-10-18
forum: General Help
---

### Post by Andy06 on 2010-10-18
We're trying to replace XP with a XP/Ubuntu dual boot on a bunch of old desktops (P4, 512MB RAM) and IDE drives. Unfortunately I'm not old enough for experience with IDE drives and the whole master/slave thing ;)

I do not want to install Ubuntu on same disk as XP and use GRUB because the transition needs to be seamless with as little margin for error as possible and enabling the users to boot into either OS on a separate disk

So I've decided to plug in another old IDE HDD into each desktop and install Ubuntu on that. Each desktop is equipped with a Cable Select cable with clear Master and Slave labelling.

So what should I do w/ regards to the Jumper settings? What about bootloader? Should it go into the slave Ubuntu disk? Can Ubuntu be made master and then offload the booting to XP through GRUB somehow (whilst leaving XP's disks untouched)?

Thanks a lot guys

---

### Post by garyed on 2010-10-18
I would recommend keeping Windows on the master & Ubuntu on the slave.
Windows can some times get confused if its not on the master drive.
I have all three of my desktops set up that way with no problems.

---

### Post by Andy06 on 2010-10-18
Ok. Will do so.
Where do I install the bootloader? I don't want to touch the XP drive at all. I know GRUB can be made to hand off booting to another drive's bootloader but if Windows is master and GRUB is on slave, then?
I guess I can look at the BIOS as well and set the boot priority there.

I have a bunch of different ways I am considering and its so confusing :)

---

### Post by garyed on 2010-10-18
I'm not sure what boot loader you're talking about but Grub will normally install itself to the MBR of the first drive sda1 or hda1 which should be your Windows drive.

---

### Post by nlneilson on 2010-10-18
Install under XP with WUBI.

Different hard drive, cables, etc. makes my head hurt, I wasted too much time tinkering with that.

---

### Post by garyed on 2010-10-18
I know nothing about a wubi install but I would think you would be defeating the purpose of having a second drive for Ubuntu if you're going to
do a wubi install.

---

### Post by Andy06 on 2010-10-19
Garyed,

Touching or modifying the XP install in anyway (such as overwriting its bootloader with GRUB) is not an option since it is not my computer I am messing with here :D

Ubuntu gives you the option of installing the bootloader to a partition/drive of your choice under "Advanced settings" in Ubiquity.

This could mean I could use GRUB to detect the presence of another disk and hand off booting to the XP bootloader (chain loading?) or alternatively, use the BIOS to set boot disk priority.

What would you guys recommend?

@nlnielson

Wubi installs are not "true" installs, I don't want to sell Ubuntu short :) 
It's a bit like running it in a VM

---

### Post by garyed on 2010-10-19
I not sure I understand what you're wanting to do. Even if you don't install grub to the mbr of the windows disk you'd still have to modify its boot loader in some way to be able to get into Ubuntu. There are quite a few tutorials around for modifying the Windows bootloader but it doesn't sound like the option you're looking for. Using the bios to change the drive order depending on which OS you want to boot from would work but you would have to make sure every time you got done with Ubuntu to change the bios order back for whoever else might use the computer. What about just making a grub boot disk (floppy,CD or usb) & only use that when you want to boot to Ubuntu. Thats the only way I can think of that you could do it without modifying anything on the Windows partition.

---

### Post by Andy06 on 2010-10-19
Garyed,

Basically I want to dual boot XP/Ubuntu without so much as touching XP even slightly. (hence the 2nd disc).

I was intending to use the BIOS to *always* boot Ubuntu first. The users merely need XP as a fall-back, Ubuntu is their new default OS. I don't think modifying the XP bootloader in anyway is necessary. Ubuntu can detect other discs and OSes on it.

What is the best way to manage dual booting from separate discs? GRUB on XP disc? GRUB on Ubuntu disc? BIOS? Or some 4th option?

Thanks

---

### Post by oldfred on 2010-10-19
Computers that are older and only boot IDE drives still use master/slave and will only boot the primary master. The BIOS is just smart enough to jump to the MBR of the primary master. If you absolutely do not want grub in the MBR of the windows drive you will have to make the Ubuntu drive master.

Windows prefers to be the first drive but will work from the second. But grub usually installs a map command (old grub) or mapdevice command to make windows think it is still drive 0 when it is drive 1. I would try that first. If the mapping is set up it should work.

If you have issues post this after your have both drives setup.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

If you want to go old school you can create a boot floppy that starts Ubuntu on the second drive.

---

### Post by Andy06 on 2010-10-19
Nah I can't do anything even mildly complicated. The people I am doing this for would not appreciate the jumping through hoops. I need to make it painless.

I will give it a trial run in the coming week and post back with any problems :)

---

### Post by Schrute Farms on 2010-10-19
You asked about the jumper settings.  Set them both to CS for cable select.

I'm no guru, but I think the easiest thing for you to do is to let the Ubuntu installer put GRUB on the windows disk, which should be set up as master.  Trying to do anything else will make things way more difficult.  Like everyone else said, Windows works best as master, and it is easiest if GRUB is on the boot drive.
Worst case scenerio, if you need to put the XP drive back the way it was, you can boot with an XP cd, go into the repair console and type "fixmbr".  When you reboot, the computer will boot into Windows normally.

---

