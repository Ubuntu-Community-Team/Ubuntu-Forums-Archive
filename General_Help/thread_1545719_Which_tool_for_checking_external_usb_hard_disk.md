---
title: "Which tool for checking external usb hard disk?"
date: 2010-08-04
forum: General Help
---

### Post by vickoxy on 2010-08-04
Hi,
is there any simple tool in Ubuntu to check my WD External USB HardDisk?

---

### Post by chopinhauer on 2010-08-04
> **vickoxy said:**
> 
is there any simple tool in Ubuntu to check my WD External USB HardDisk?

Actually there are two. :-)

**badblocks** to check for faulty sectors on your disk and **fsck** to check for file system corruption (and correct it).

Both take the device name (/dev/sdXX) as a parameter.

---

### Post by vickoxy on 2010-08-04
badblocks is not in synaptic, or? Is there any GUI Tool?

Subquestion: is disk formatting enough  to erase all data on my drive that i want to sell away?

---

### Post by FahadMKS on 2010-08-04
Ubuntu itself has a disk checker in it.

Login to the computer as Root >> then select System >> Administration >> Disk Utility.

There select the external hard Disk and then unmount it and then you can check the Disk.

---

### Post by vickoxy on 2010-08-04
> **FahadMKS said:**
> Ubuntu itself has a disk checker in it.

Login to the computer as Root >> then select System >> Administration >> Disk Utility.

There select the external hard Disk and then unmount it and then you can check the Disk.

Maybe stupid question; but how to login as root? I should logout, then at login select some option, or should i restart computer?
Disk Utility checks external drives too?

Thanks

---

### Post by chopinhauer on 2010-08-04
> **vickoxy said:**
> 
I should logout, then at login select some option, or should i restart computer?
Disk Utility checks external drives too?


'Root' is a misnomer. You should login as a user in the 'admin' group (first user already is) and the disk utility will check if you have 'sudo' permissions when necessary.

Disk Utility checks everything: external drives, LVM volumes, RAID arrays.

---

### Post by vickoxy on 2010-08-04
Ok, i choose option - see picture: "check data system" (i have german version). After 1 Sec. it was over and it said something as "all clean". Is that really enough?

---

### Post by FahadMKS on 2010-08-04
It is not an Stupid Question. :)

Root is the Most Powerful Admin user of the Ubuntu OS

You may select the option as Users and select the user and change the password for root and then logout of the current user and then select the option as Other and then enter the username as root and the password that you had just changed.

You can try with the normal user and if it prompt to get to the root, then only you may try to login as Root.

---

### Post by vickoxy on 2010-08-04
Thanks. And subquestion:
> Subquestion: is disk formatting enough to erase all data on my drive that i want to sell away?

---

### Post by FahadMKS on 2010-08-04
Sure, it is.

You can also use a disk Shredder tool before selling the HDD if you have any releavent data like passwords or CC numbers.

U can make use of the command # [B]shred [COLOR=#000099]-v[/COLOR][COLOR=#990000]f[/COLOR][COLOR=#000099]z[/COLOR] [COLOR=#990000]-n[/COLOR] 100 /dev/hda

[/B]Here [FONT=courier new]/dev/hda[/FONT] is my whole hard disk.
And I am asking shred to make (**-n**) 100 passes by overwriting the entire [[COLOR=#003399][COLOR=#003399 ! important][FONT=arial][COLOR=#003399 ! important][FONT=arial]hard [/FONT][/COLOR][COLOR=#003399 ! important][FONT=arial]disk[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html#") with (**-z**) zeros. 
And shred program (**-f**) forces the write by changing the permissions wherever necessary.

---

### Post by utilitytrack on 2010-08-04
to **vickoxy**

beware when use utilites for checking storage devices. don't forget unmount them before and read [FONT=Courier New]man fsck[/FONT] and [FONT=Courier New]man badblocks [/FONT]carefully. also [FONT='Courier New']smartctl --attributes /dev/disk[/FONT] can help you

---

### Post by vickoxy on 2010-08-04
> **FahadMKS said:**
> Sure, it is.

You can also use a disk Shredder tool before selling the HDD if you have any releavent data like passwords or CC numbers.

You mean, some options also in disk utilities (sorry, i use german language...:-?

Well, there is nothing really important, family photos, some movies (.iso)...

Thanks for help...:popcorn:

---

### Post by chopinhauer on 2010-08-04
> **vickoxy said:**
> 
Is that really enough?


That just means that the data on the disk are ok, not that the disk is physically sane. If you want to sell the disk, you should run **badblocks**:
```
sudo badblocks /dev/sdb
```
and check for errors. 'sudo' is to run the command as the user 'root'.

You can also check the SMART data in disk utility.

---

### Post by vickoxy on 2010-08-04
> **FahadMKS said:**
> Sure, it is.

You can also use a disk Shredder tool before selling the HDD if you have any releavent data like passwords or CC numbers.

U can make use of the command # [B]shred [COLOR=#000099]-v[/COLOR][COLOR=#990000]f[/COLOR][COLOR=#000099]z[/COLOR] [COLOR=#990000]-n[/COLOR] 100 /dev/hda

[/B]Here [FONT=courier new]/dev/hda[/FONT] is my whole hard disk.
And I am asking shred to make (**-n**) 100 passes by overwriting the entire [[COLOR=#003399][COLOR=#003399 ! important][FONT=arial][COLOR=#003399 ! important][FONT=arial]hard [/FONT][/COLOR][COLOR=#003399 ! important][FONT=arial]disk[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html#") with (**-z**) zeros. 
And shred program (**-f**) forces the write by changing the permissions wherever necessary.

"Shred" seems to be a good option, but it would take a very long time to repeat-what - 100 times the procedure? Or it does it only once?

---

### Post by chopinhauer on 2010-08-04
> **vickoxy said:**
> "Shred" seems to be a good option, but it would take a very long time to repeat-what - 100 times the procedure? Or it does it only once?

Yes, 100, may be too much, I'd say 10 should be enough (even with professional hardware recovery tools).

---

