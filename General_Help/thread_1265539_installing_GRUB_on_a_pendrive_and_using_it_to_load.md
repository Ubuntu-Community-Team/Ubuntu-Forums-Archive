---
title: "installing GRUB on a pendrive and using it to load ubuntu (installed on a hard drive)"
date: 2009-09-13
forum: General Help
---

### Post by simon.hanna on 2009-09-13
I have both windows Vista and Ubuntu installed on my notebook...
By default MBR is loading Vista...

I don't have Ubuntu listed in MBR...

What I want is to install grub on a Pendrive and when I insert it and start my notebook grub runs instead of MBR and boots ubuntu...

Is that possible??!!

---

### Post by ajgreeny on 2009-09-13
It certainly is!

Run the live ubuntu CD and then, with the pendrive attached, run sudo fdisk -l to find out the device name of the pendrive, most likely sdb, if you only have one hard disk.

Now, still in the live CD, open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu.  Hopefully this will report the same device name as fdisk did, but this time as hd1.  If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd1,1) ,probably]
then:
    ```
setup (hd1)
```
Use hd1, etc as appropriate for your pendrive.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.  Set your machine to boot to the pendrive first, of course, which I assume you had already done.

Good luck.  If it does not work, come back again.

---

### Post by simon.hanna on 2009-09-16
hmmm.. i tried it but i failed... i have a notebook with two harddrives... i tried all "setup (hdx)" combinations, but all it did was that it installed it on my harddrive not my pendrive....

---

