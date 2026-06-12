---
title: "my win98 parttion won't boot"
date: 2006-06-02
forum: General Help
---

### Post by MetalHannes on 2006-06-02
Hello,
I'va had Ubuntu 6.06 installed on my pc and a Fat32 partition nearby.
After installing win98 i wasn't able to boot Linux anymore.
I've reinstalled Grub with inserting the Breezy Badger install CD and starting up with "rescue", as said in some threads and the wiki.
Then i rebooted and i was able to start Linux but not windows!
There is a entry which says Win 95/98/ME but it only goest to
"Grub Loading Stage 2......." or something like that and then returns to the selection menu (Where i can select which Kernel to boot).
I've tried 

sudo grub-install /dev/hda1 and it gave xfs_freeze error.

What should i do?

Hannes

---

### Post by nixt on 2006-06-02
The xfs_freeze error is harmless if I recall correctly.

Getting Win98 to boot should be as easy as adding a new boot entry in /boot/grub/menu.lst

Please do a sudo fdisk -l /dev/hda and report the output...

---

### Post by nixt on 2006-06-02
See if running 

sudo update-grub

helps

---

### Post by MetalHannes on 2006-06-02
thx for the quick answer
sudo update-grup didn't change anything.
here the outputs frim sudo fdisk -l /dev/hda

Disk /dev/hda: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device        Boot   Start       End       Blocks          Id    System
/dev/hda1   *        1              305       10482381    c     W95 FAT32 (LBA)
/dev/hda2            1306        2438      9100822+   83   Linux
/dev/hda3            2439        2491      425722+     5     Extended
/dev/hda5            2439        2491      425691        82   Linux swap / Solaris

---

### Post by Fass on 2006-06-02
Append the following to the end of your /boot/grub/menu.lst

```
title           Microsoft Windows 98
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by givré on 2006-06-02
And what is your /boot/grub/menu.lst.

If it is not already there, you should had an option for windows at the end of the file like that :
```

title           Windows
root            (hd0,0)
makeactive
chainloader     +1
```
If there is something like that verify your root line:
For hda1 (where is your windows partition) it should be (hd0,0)

Edit : Fass was fater ;)

---

### Post by MetalHannes on 2006-06-02
At the End of /boot/grub/menu.lst there are the lines that Fass wrote
Is the savedefault necessary? Should i use it??

---

### Post by nixt on 2006-06-02
It is alright to leave savedefault out..

---

### Post by MetalHannes on 2006-06-02
leaving savedefault  out didn't change anything either...

---

### Post by givré on 2006-06-02
Which tip did you do from [https://wiki.ubuntu.com/RecoveringGrub](https://wiki.ubuntu.com/RecoveringGrub) when you recover grub. 
Actually you have two tips :

1.Using the LiveCD while preserving Windows Bootloader
2.Using the LiveCD and Overwriting the Windows bootloader

I think the one you should do is the second one, dapper default installation seems to right in th MBR

Let's try that and see what's happen.

---

### Post by MetalHannes on 2006-06-02
I haven't used the live CD at all i've done it with the "normal" install CD
I guess i overwrote the windwos bootloader

---

### Post by givré on 2006-06-02
Not sure because you did it with the 5.10 install CD and not the with the 6.06 install CD.

Anyway, you should try to put grub in the MBR, if it's not already done.
So let's go, open a terminal and type 
```
sudo grub
```
you will have a prompt, just type in
```
root (hd0,1)
setup (hd0)
quit
```

Not sure that it resolve your problem, but it is just a try, and it's safe to do it.

---

### Post by MetalHannes on 2006-06-02
When i typed setup (hd0) th following error appeared:
Error 23: Error while parsing number

Also when typing

root (hd0,1)

it said filesystem ext2fs isn't it supposed to be FAT32?

---

### Post by givré on 2006-06-02
[QUOTE=MetalHannes]
Also when typing

root (hd0,1)

it said filesystem ext2fs isn't it supposed to be FAT32?[/QUOTE]
No this is normal because it have to be the partition where you have your /boot directory, and this one is one hda2 (i.e. (hd0,1) for grub )

but your error is more interesting, it seems it don't understand what you type.
Try to retype it, it should be exactly: setup (hd0)

---

### Post by MetalHannes on 2006-06-03
ok sry must have made a typing mistake, here the outputs:
>  Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.


But i recognized that even after i've done this, the commands when he wants to start win98 begin with > root(0,0)

Thank you so much

---

### Post by givré on 2006-06-03
[QUOTE=MetalHannes]
But i recognized that even after i've done this, the commands when he wants to start win98 begin with 

Thank you so much[/QUOTE]
Yeh of course but you configure grub to be able to boot your linux partition, so it will need your linux device. Be able to boot windows (or anything else) is an option you add in your source.lst (in our case it is done automaticly at the installation)

So how is it going know

---

### Post by MetalHannes on 2006-06-03
Nope still no change
/edit: I have reinstalled windwos but now i can't install grub!
I can't start the rescue mode on the Dapper CD an on the Breezy CD it haven't made any chages...

---

