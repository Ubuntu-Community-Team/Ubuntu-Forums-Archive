---
title: "Grub error: no such partition / grub rescue"
date: 2012-07-31
forum: General Help
---

### Post by dezdezdez on 2012-07-31
Hello,

I googled around this issue and most threads that had people with comments about unsolved issues should just open a new thread. Thus here I am.


the issue:

when I boot my computer, after the motherboard splash screen I get the following:


GRUB loading
error: no such partition
grub rescue> ls
(hd0) (hd0,4) (hd0,3) (hd0,2)
grub rescue> set
prefix=(hd0,5)/boot/grub
root=hd0,5
grub rescue> _


cause:

So it looks like the prefix/root are pointing at the wrong partition, so I'm not entirely sure if my partition is now dead, or what... 

Basically I had dual boot between Ubuntu and Windows 7.

I was in windows last night and it suddenly started closing all the programs and shutting down, then when I restarted it, I was at this point.
My strongest guess would have to do with bad sectors in the boot section, but I'm looking for some insight into what tools to use to diagnose this and to fix it...

thanks for your help, let me know what other info you need!

---

### Post by raja.genupula on 2012-07-31
you can use Grub recovery to restore your grub . look at my signature .

---

### Post by OM55 on 2012-07-31
Hello dezdezdez,

If you get the 'grub-rescue' prompt, it means that your grub info is corrupted and you need to fix it, which is pretty easy to do. This is how you can fix it (you will need the Ubuntu Live CD or USB Key):

Symptom:
========
After boot we get the prompt:

error: file not found.
Grub rescue>-


Problem:
========
The grub information on disk has been corrupted and the system can not boot from the proper partition

Solution:
=========
1. Boot with Ubuntu Live CD

2. Open terminal (command prompt)

3. Type: sudo fdisk -l

You will get a list of partisions, similar to the following list:

/dev/sda1 13 102400 de Dell Utility
/dev/sda2 * 13 1926 15360000 7 HPFS/NTFS
/dev/sda3 1926 30892 232676566 7 HPFS/NTFS
/dev/sda4 30893 60802 240245761 5 Extended
/dev/sda5 30893 59584 230467584 83 Linux
/dev/sda6 59585 60802 9777152 82 Linux swap / Solaris 

Ubuntu partition is the one with the name "Linux" (not necessarily the one with the star, although could be).
On this case is on '/dev/sda5' so we have to mount it:

4. sudo mount /dev/sda5 /mnt
   (replace 'sda5' with the partition name in your case)

5. And then install grub:
   sudo grub-install --root-directory=/mnt /dev/sda

6. Reboot and verify that all is working fine.

---

### Post by Bucic on 2012-09-10
I did all as per section 13 here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I still get only the bash prompt...

I also tried the *live CD > boot repair > recommended* way. Same.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by YannBuntu on 2012-09-12
Hello

What is the URL that appeared when doing *live CD > boot repair > recommended* ?
(if you don't remember do it again)

---

