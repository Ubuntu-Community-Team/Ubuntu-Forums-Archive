---
title: "getting rediculous"
date: 2010-01-01
forum: General Help
---

### Post by martinshort on 2010-01-01
ok...  this is geting really stupid now. 

after a week trying to get a shitty broadcom card to work as expected i found a post somewhere here that advised to use the system upgrade tool to upgrade all software and then trying installing the old driver that came with this installation of 9.10....

so i did that. now i just get a shell grub prompt that cant undertand what the effing thing wants because any of the commands are usless. it wants a kernel. where the f is the effing kernel to tell grub to boot using that one?!?

---

### Post by martinshort on 2010-01-01
all i see is:
sh:grub>

one of the possible commands is boot. when i do that i get:

error: no loaded kernel

where is the kernel and how do i tell grub to load it?

---

### Post by pastalavista on 2010-01-01
Install 9.10 again in MANUAL mode (with the live CD) and at the partition screen, UNCHECK the format boxes.

---

### Post by martinshort on 2010-01-01
this is installed from an windows installer on a hp mini. there is no cd/dvd drive.

---

### Post by pastalavista on 2010-01-01
> **martinshort said:**
> this is installed from an windows installer on a hp mini. there is no cd/dvd drive.
in that case, use the live USB...

---

### Post by martinshort on 2010-01-01
what do the format boxes do?

usb. does that mean that i have to have an external cd drive or a stick?

---

### Post by pastalavista on 2010-01-01
> **martinshort said:**
> what do the format boxes do?

usb. does that mean that i have to have an external cd drive or a stick?
If the format boxes are checked, it erases everything that was on the partition. With them not checked, it only reinstalls the files, overwriting the original system files that are in place but nothing else is changed. Updates will be gone though.

I'm guessing you installed Ubuntu with Wubi in Windows. Yes, you'll need a flash or regular USB drive with Ubuntu on it. You might also try a [SupergrubDisk]("http://www.supergrubdisk.org") on the same kind of drive.

I've heard there are ways to boot Windows from an external drive but I don't know how you can put it on a flash drive.

---

### Post by martinshort on 2010-01-02
i don't have any of those handy,

i did reinstall from wubi. same result. 
thought i think now that this machine has a faulty chip.
i did a few pings on the windows side and the dropout rates seem to be consistent. 
so i'm going to take this thing back to the store tomorrow and see if i can get one with a chip that doesnt drop.

thanks for you tips though...

---

