---
title: "grub load error 17"
date: 2010-03-31
forum: General Help
---

### Post by rejuvenate on 2010-03-31
hi ,
my system have 3 OS's ,it has window vista in (/dev/sda3 -C:/drive and /dev/sda2 - D:/drive), and ubuntu 9.04 which i installed when i am new to ubuntu (/dev/sda5-ext3 ) and ubuntu 9.10 (/dev/sda6/ -ext3 and /dev/sda7 -linux-swap) ..in order to free the ubuntu 9.04 space i deleted the swap of ubuntu 9.04 drive using disk utility(system->administration->disk utility).. when i restarted it show me an 

grub1.5 loading 
error 17

i searched for the help i am unable to solve it ...i have attached the menu.lst from ubuntu9.10 and the details of partitions....thanks in advance i need an urgent help.....

---

### Post by byStanderone on 2010-03-31
hi,
...which 'os' did you install the last, is it karmic? if so, grub2 is the default bootloader in karmic, which leads me to wonder if you have intentionally installed grub1.5

---

### Post by kaizokuroof on 2010-03-31
I think what you've done is messed up the boot order in Grub, I had the same problem, can't remember how I fixed it. You COULD reinstall Grub completely using a live CD/USB.

Or you could figure out your order. I'm not sure how to do this as I'm still new to Linux but I hope this helped.

kaizoku roof.

---

### Post by rejuvenate on 2010-03-31
> hi,
...which 'os' did you install the last, is it karmic? if so, grub2 is the default bootloader in karmic, which leads me to wonder if you have intentionally installed grub1.5

i have updated from 9.04 to 9.10, i didn't made any change with grub at that time........but it doesn't have any thing with that.........

---

### Post by Objekt on 2010-03-31
This one should be an easy fix.  It is actually fairly common, when using the older version of GRUB, as you are.  I have had to fix it on my own computers a few times.

Try this: boot a live CD, and edit the "root" lines of the Ubuntu entries in your menu.lst file to:

```
root		(hd0,6)
```

I'm pretty sure that would let you boot Ubuntu again.  You appear to have Ubuntu 9.10 installed on partition sda6.  

If 6 doesn't work, try other values (5, 7, etc.).  You won't break your system worse, and you might fix it.

Here's why: Because you deleted the Ubuntu 9.04 install, the number of partitions on your disk is now different.  GRUB is looking in the wrong place.  That's one of the problems with older GRUB: the numbering of partitions can change, and when it does, GRUB looks in the wrong place for boot files.

---

### Post by rejuvenate on 2010-04-01
thanx for the help.....i found the solution already..just for others i am putting it here.....

GRUB is generally lost due to Windows install or if your MBR gets erased. Follow the simple steps given below to restore GRUB.

1. Boot your computer using a Linux live CD.

2. Open a terminal and type,

liveuser@liveuser-laptop:~$ sudo grub

This gives you the grub prompt.

3. To inform the GRUB about the location of the GRUB files, we should know it ourselves first. Generally, it is (hd0,1), which means hda (primary controller master) in the second partition. 

If you know where they are, type , 

grub> root (hd0,1) 

Else to find out, type,

grub> find /boot/grub/stage1 

this is with a relation of n to  n-1 i,e if ur ubuntu is installed in /dev/sdaX then it will be  mapped to (hd0,X-1)

where hd0 is the first hard drive similarly it can be hd1,hd2 for further any hard drives...
and X is the partition number on that hard drive...

4. Then install it on hd0 (or any other hard drive in your case), which is the MBR of the first HDD.

grub>setup (hd0) 

this will just install the grub again..

5. To quit, type

grub> quit

6. Reboot your machine.

liveuser@liveuser-laptop:~$ reboot

The GRUB menu appears on system reboot.

---

### Post by byStanderone on 2010-04-01
...happy to know you did your thing, sail on.

---

