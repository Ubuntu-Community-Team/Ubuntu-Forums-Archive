---
title: "Install problems with Sony GRT816S"
date: 2010-11-09
forum: General Help
---

### Post by acjones100 on 2010-11-09
No doubt, these sorts of questions get asked all the time so Im sure some of you talented Ubuntu experts and enthusiasts can help me.
 
Ive got a Sony GRt816S laptop which Im trying to install 10.10 on to a freshly formatted hard drive. 
 
I downloaded the file burnt it to disk  and tried to run it.  I get to the first screen where It asks me if i want to run for CD, install or do memory check. - memory checks works fine but the install and run from CD options  just hang before I get anywhere near an actual install screen (or anything that remotely looks like one) 
 
I just see a purple ubuntu screen with 4 dots which alternate between red and white ocassionally. I've left it running over night and nothing happens.
 
I read on the forum that it might be the original file, so tested it on a different pc and it worked fine.
 
I know what Im doing with PCs but am a total novice when it comes to Linux, ubuntu or anything thing non-windows related ( I know shocking ) 
 
 
Any help would be greatly appreciated

---

### Post by nbala.iyer on 2010-11-09
hi .. ensure that check sums are fine after the download of ISO , i got installation issues due to messed up check sums.. :)

---

### Post by old_dog on 2010-11-09
I don't if this will help but it may make you feel better!
Sony laptops seem to be more than a trifle idiosyncratic!!!
Can't remember the model number but ended up creating an install DVD(would not boot from CD!!!) booted up from DVD installed 10.04 all tickety boo! 
Best of Luck

---

### Post by acjones100 on 2010-11-09
bit of an update, if I click esc button on the screen where it seems to freeze I see the following command line 
 
 
stdin: error 0
/init: line 7 : can't open  /dev/sdb

---

### Post by savastux on 2010-11-10
Just for the record, I'm facing the same problem here:

CD's images are OK. Checksum OK.


Tried with 10.10 64 and 32 bits.

This is on a HP Desktop (p6000)


Any clues?

---

### Post by acjones100 on 2010-11-11
Update :- 
 
I took the hard-drive out of my Sony - put it in a Hard Drive Caddie, plugged it into a Dell PC - installed the software, made sure it worked on dual boot. 
I have now put the Hard-drive back into my sony, it still doesnt work, it seems to boot to a blank screen. 
 
if I load in Recovery mode using the failsafe graphics mode I get the following error 
 
 
(EE) VESA(0) : No valid Nodes
(EE) screens found, but none have a useable configuration
 
Fatal Server error
no Screen Found 
 
 
 
I would assume I need to update the graphics driver, but dont know where to start (graphic card on my laptop is Nvidia FX go5600)
 
 
 
Help !! Im getting quite annoyed by it now !

---

### Post by nbala.iyer on 2010-11-11
Hi , 
 
From the grub menu type 'c' to enter commandline .. 
grub> insmod ext2
grub> insmod ntfs
grub> insmod fat
grub> insmod video
grub> linux /boot/vmli (tab for choosing the correct version )
grub> initrd /boot/initrd (tab for choosing the correct image )
grub> boot
 
this will give complete details of where the grub is getting stuck during the quiet splash mode.
rgds,

---

### Post by P4man on 2010-11-11
Check my signature, boot with "nomodeset".
If those laptops have "nvidia optimus" also make sure you set the bios to disable optimus. Either set it to intel IGP, or to nvidia discrete GPU, but not optimus. Its not compatible with linux.

---

### Post by savastux on 2010-11-13
Well, I've managed to work things out here.

I've created a bootable USB disk with the same image I was burning.
My desktop recognized flawlessly and I was able to use LiveCD or install Ubuntu.

Maybe if you try this, you can install it too.

Regards,
Savastux

---

### Post by savastux on 2010-11-13
To find out your hardware, I would suggest 2 commands:

```

dmesg

```

and

```

lshw

```

This should give you a head start so you can install the right driver.

Regards,
Savastux

---

