---
title: "Sorry - Dumb Question, Creating Grub2 from Scratch"
date: 2009-12-16
forum: General Help
---

### Post by Quarkrad on 2009-12-16
For some reason I want to have a backup/restore capability for my dual boot (9.10 and winXP) system (I can backup sda1 and sda2 to my 2nd sdb HD).  Whilst rebuilding my whole PC I have further researched that the problem seems to be (for a newbie) that ext4 is not supported by commercial products (yet) and there is an issue with Grub 2 when restoring partitions.  It seems my best bet at the moment is to use Clonezilla to backup and restore either partitions as and when.  BUT when I do this it appears I will have to rebuild Grub 2 inorder to have a working machine again.  Appreciate some advise on what read that will clearly explain how I rebuild Grub 2 after a restore.  I will have 9.10 0n sda1 and winXP on sda2.

---

### Post by akakingess on 2009-12-16
No such thing as a stupid question first of all, but see if this helps if you haven't already read it, as I have had to refer to it myself a few times: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Quarkrad on 2009-12-16
Thanks - I have read this and got into all sorts of trouble yesterday.  Hence having to rebuild complete PC - doing it now!  Is it the case then after a restore and grub isn't there anymore, in theory you - boot via Live CD.  Install grub with something like sudo apt-get install grub (sorry cannot remember the exact command) and all will be well?   Yesterday I went through this procedure and just could not Grub to see my xp partition.  Perhaps I did something wrong but all sorts of horrors then happened and the whole PC went bang.  Pity with Linux/Ubuntu you cannot put the live CD and in and go fixboot and/or fixmbr as per windows.  Generally this (fixboot/fixmbr) gets you out of trouble most times.  Grub is more of a challenge.  It certainly caused me a heep of trouble yesterday!  (As a note - and I have recommended Ubuntu to a number of friends. A pity 9.10/ext4 has been released and there is not an easy way of being able to backup and restore partitions.  Surely this is something most people (should) do to safeguard their data).  Acronis True Image in the windows world worked a treat - pity there is nothing for Ubuntu.

---

### Post by akakingess on 2009-12-16
In theory, yes you could do that via LiveCD, but what I don't know if there is a way to "rebuild" it without having to completely reinstall it. Sorry I'm not too much help, just trying to give info where I think it may assist you.

---

### Post by Quarkrad on 2009-12-16
Ok - have rebuilt pc. U9.10 on sda5 and winXP on sda1.  PC boots fine and grub2 working OK.  Made an image of sda5  and then restored.  As last time pc boots to a grub screen but it just sits there as grub>    I booted to live CD and followed instructions (**[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)**) on reinstalling grub, specifically sect 11.1 - it went Ok until I got the following:

[B]root@ubuntu:/home/ubuntu# sudo mount /dev/sda5 /mnt
root@ubuntu:/home/ubuntu# sudo grub-install --root-directory=/mnt/ /dev/sda5
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly[/B]

any idea on what to do next?

---

### Post by Quarkrad on 2009-12-16
Help - having restored Ubuntu what do you do now?  Grub> ..........

---

### Post by philinux on 2009-12-16
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

I would give this a go.

---

### Post by drs305 on 2009-12-16
> **Quarkrad said:**
> it went Ok until I got the following:
root@ubuntu:/home/ubuntu# sudo mount /dev/sda5 /mnt
root@ubuntu:/home/ubuntu# [COLOR="DarkRed"]sudo grub-install --root-directory=/mnt/ /dev/sda5[/COLOR]
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

any idea on what to do next?

It looks like you didn't have the command correct, unless you were specifically trying to install it to sda5:
> sudo grub-install --root-directory=/mnt/ /dev/sdX

Generally GRUB2 prefers to install to the MBR (sda, sdb, etc) rather than a partition (sda5, etc). So the command for most users should be run, for example, as:
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

---

### Post by Quarkrad on 2009-12-16
No luck so far by either method.  Here is the output of fdisk -l

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c26fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276       48641   380467395    f  W95 Ext'd (LBA)
/dev/sda5            1276        3825    20482843+  83  Linux
/dev/sda6            3826       26266   180257301    7  HPFS/NTFS
/dev/sda7           26267       47890   173694748+   7  HPFS/NTFS
/dev/sda8           47891       48641     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005a4cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdb5               2       22948   184321746    7  HPFS/NTFS
/dev/sdb6           22949       60801   304054191    7  HPFS/NTFS

I have two HDs  sda has winXP on sda1 and sda6 with ubuntu on sda5 - the sdb HD is for storage - I have the image of sda5 that I restored on sdb 5.  When I built the PC I installed winxp on sda1 first followed buy 9.10 on sda5 and than winxp again on sda6.  Before the restore this all worked fine including grub2.  Many thanks for your help.

---

### Post by Quarkrad on 2009-12-17
Wow - thanks Philinux.  Your post solved my problem - I just substituted my sda for sda1 and it all worked.  Many thanks.

---

