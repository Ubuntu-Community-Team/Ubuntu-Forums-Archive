---
title: "Formatting flash drive"
date: 2010-02-26
forum: General Help
---

### Post by malikge on 2010-02-26
Hello I want to know how to format the Flash drive. I have found that the following command can format it.

[INDENT]sudo mkfs.ext3 -m 0 /dev/sda1[/INDENT]

but then the flash drive cannot be run on Windows. I want to know how to format it and still it can run on Windows. 

Other thing is that the flash drive can also be accessed from 
[INDENT]File System>> media>> disk(the name of the flash drive)[/INDENT]
can I format it from here???
Thanks.

---

### Post by johngreth on 2010-02-26
If you right click the drive on the desktop and click "format", you can do it there. to go between platforms you need FAT file system. You could also click "Disk Utility" to select a more specific filesystem.

---

### Post by redbook4574 on 2010-02-26
which version of ubuntu do you use,

if 9.10 you can use disk utility or gparted

previous version use gparted (my preference).

---

### Post by zbirdman777 on 2010-02-26
You can use Gparted to format it. With the flash drive plugged in open GParted and at the top right theres a drop down menu that lets you select different Hard Drives. Select your flash drive from the drop down menu and Gparted will scan it. 

You should delete it to create free space and format it. If it is unformatted no OS will read it. 

I suggest fat32 (vfat) it works on most things.

---

### Post by malikge on 2010-02-26
Thanks everyone for replying, I think I am gonna go with zbirdman777
and use "vfat". I have read about gparted but I want to do this through command line.
Thanks again.

---

### Post by derrick81787 on 2010-02-26
> **malikge said:**
> I have read about gparted but I want to do this through command line.
Thanks again.

It's definitely possible to do on the command line, but (in my opinion) not quite as easy.  Gparted is basically a nice GUI version of the command line program parted.  Type "man parted" to learn more about it.

- Derrick

---

