---
title: "Boot W7 directly from Grub?"
date: 2011-07-08
forum: General Help
---

### Post by Budisha on 2011-07-08
I installed Ubuntu on w7 using Wubi and i set in w7 that it on startup automatically boots Grub without asking.
Now when im in Grub and when i select Windows 7 (loader) it goes black and returns to Grub so i cant boot w7 at all.

---

### Post by bcbc on 2011-07-08
You set the timeout in W7 to zero?

So this is what is happening:
Boot computer
Windows Boot loader
Windows Boot Sector
Windows Boot manager - timeout 0 go to Ubuntu
Grub2 menu
You select Windows
Windows boot sector
Windows boot manager - timeout 0 go to Ubuntu
...

When you boot try hitting F8, or the up arrow key, or anything to interrupt the Boot manager. If this doesn't work...

You need to boot a windows repair CD (or from your install DVD to a repair prompt) and try to modify the timeout using bcdedit, change the default entry, or rebuild the bcd.

---

### Post by Rubi1200 on 2011-07-08
Hi and welcome to the forums Budisha :-)

As bcbc pointed out, you need to change the timeout.

Here are some more instructions on how to do this:
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)

See Option 2 about using the repair/recovery disk.

You need to follow the steps and choose the command prompt option.

Then do the following:

Open the command window and run "bcdedit" (without quotes); this will list the BCD info. 

In the "Windows Boot Manger" section I assume that the timeout value is 0. 

To change it to 30 seconds you would run "bcdedit /timeout 30" (again without the quotes). 

Exit the command window and reboot. You should have the boot menu again.

---

### Post by Budisha on 2011-07-09
I tried booting in safe mode by pressing f8, pressing f5 and pressing the up arrow key but it didnt work, it went directly to grub.
I also tried making a bootable USB with the system repair disc image on another pc and i booted the USB on that pc, but when i tried it on my pc by pressing f12 and selecting USB it didnt work.

Edit: after doing "sudo update-grub2" the usb showed up in grub, but when i select it, it says "Unknown command 'drivemap'
Here's the code in grub.cfg:
```

menuentry "Windows Recovery Environment (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 00dc-7c41
    drivemap -s (hd0) ${root}
    chainloader +1
}

```

Edit2:
I found a empty DVD and downloaded the recovery disc image. Booted it up, started command prompt and fixed it with bcdedit /timeout 30

Thanks for the help

---

### Post by Rubi1200 on 2011-07-10
> Edit2:
I found a empty DVD and downloaded the recovery disc image. Booted it  up, started command prompt and fixed it with bcdedit /timeout 30

Excellent! I am glad you managed to get this fixed :)

Enjoy!

---

