---
title: "Stuck in CLI"
date: 2009-11-06
forum: General Help
---

### Post by kaelonlloyd on 2009-11-06
My wubi installation of karmic koala no longer wants to work :(

The GRUB2 boot loader , for some reason deicides to go into CLI mode, without an option to enter menu mode, i have no idea on what to do.

I think this is due to an update i done earlier, ut i'm not too sure.

So if anyone knows a way to boot into a wubi partition through grub 2 CLI please reply, or if you even know how to fix the problem without the use of a live cd (I can't access my cd till tomoz)

---

### Post by P4man on 2009-11-06
Dont know how to recover a wubi. Even a live cd would be of little use I think.

You can try this to fix grub:
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot](https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot)

Other than that I can only advice you do a filesystem check in windows and next time, dont do a wubi install.

---

### Post by kaelonlloyd on 2009-11-06
Bump

---

### Post by P4man on 2009-11-06
Kind of rude to bump after 1 hour and while ignoring my post. Did you even try what I posted?

---

### Post by kaelonlloyd on 2009-11-06
Sorry didn't mean to ne rude, but i've tried checking the harddisk for corrupt sectors, all clean. Also i can't make much sense of on that link due to my limited knowledge of linux

---

### Post by P4man on 2009-11-06
It has a step by step guide and screenshots.
If there is a particular step you dont understand feel free to ask, but I doubt anyone is going to write a more detailed explanation than that doc..

read the* Command Line & Rescue Mode* section  first, then try it and report where you get stuck.

---

### Post by kaelonlloyd on 2009-11-06
I now understand what i must do, but i have 4 devices when i type 'ls'

These are:
(loop0)
(hd0)
(hd0,1)
(fd0)

I know fd is floppy, and thats all.

I don't know which is linux, or what to write when it comes to defining the root in terms od sda/sdb.

I've tried (hd0) which i guessed was just sda, when attempting to boot it goes to busy box(or busy bus, can't remember)

(hd0,1) is sda1, which returns an error and a crash when i attempt to boot.

I guessed (loop0) as sda0, which returned the same as sda

But i'm sure that ubuntu is(loop0), but what do i write for the device in terms of sda, or sdb??

---

### Post by P4man on 2009-11-07
I did some googling, it looks like grub is just  installed on your windows drive. There should be a C:\wubildr.mb for stage1. Can you confirm that file exists? 
The rest is in  C:\ubuntu\disks\boot\grub\
Can you post the contents -if any- of 

C:\ubuntu\disks\boot\grub\menu.lst

As I dont how wubi works.

---

### Post by kaelonlloyd on 2009-11-07
In my C;/ dir, i got 
wubildr
wubildr.mbr

and my C:\ubuntu\disks\boot\grub dir, is empty

If i can somehow boot into ubuntu, i should be able to run the 'update-grub' command to fix this

---

### Post by kaelonlloyd on 2009-11-07
bump number 2

---

