---
title: "Cannot boot into Ubuntu anymore?"
date: 2010-08-24
forum: General Help
---

### Post by MintPaw on 2010-08-24
Hello I started to use Ubuntu recently and I decided to also install a Windows 7 OS on my other Hard Drive

But now I'm only able to use the Windows OS. It doesn't give me a choice at boot like I thought it would.

I cannot even access my Ubuntu drive while in Windows. But I know it is still functioning because I can see it in my partition drive handling list.

But it does not register as an OS because I cannot see it in the "boot" tab or MSCONFIG.

So how do I re-enable it?

Thanks in advance. :3

---

### Post by quixote on 2010-08-25
When you install Windows (any version) second, it writes its own bootloader to the Master Boot Record (MBR) and, being Windows, doesn't think you need any other OS. :?  So you need to reinstall grub.  The instructions are [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202").  I think the "simple" method should work fine for you.  If anything's not clear, come back to this thread and ask and I'll see if I can answer it. (Grub will give you the choice to boot Windows after you reboot and run "sudo update-grub".)

---

### Post by MintPaw on 2010-08-26
Ok then this is what I have done.


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00094861

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14126   113458176   83  Linux
/dev/sdb2           14126       14594     3760129    5  Extended
/dev/sdb5           14126       14594     3760128   82  Linux swap / Solaris

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe078af87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS

```So it looks like I'll need to use sbd1. Then:

```

ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

```Weird but ok.

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb1 --force
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
Installation finished. No error reported.
```*Restarts computer without ubuntu disk*
*Starts booting into windows without choice*
*Restarts computer with disk*

```
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```I can navigate to /dev so what's the deal? I decided to mount both my drives to see if that would do anything and it didn't.

---

### Post by quixote on 2010-08-26
You did everything right, except for one small thing.  In this line```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb1
```what you really want is```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/**sdb**
```If you check the link again, you'll see they say that, but they obviously don't stress it enough.

sdb refers to the whole drive.  sdb1 refers to a partition.  What you did is successfully install grub to the **partition**, and told it to leave the MBR alone.  So Windows still owns the MBR.

Just repeat what you did, but this time using plain sdb.  reboot, run sudo update-grub, and I think that'll deal with it.

---

### Post by MintPaw on 2010-08-26
Looks like the same thing happens:

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

---

### Post by mr clark25 on 2010-08-26
were all of the outputs the same on all of the previous commands?

if not, they may help.

i know another method, but it is a little harder...

---

### Post by quixote on 2010-08-27
That error message you get suggests the system is **still** trying to find its bootable partition in the wrong place.  The earlier method was to try to get grub to look in the right place.  Since it's still not doing it, the next thing is to do it from inside grub.  Which is probably the same as the more complicated method clark25 mentioned.  It's described [here]("https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode").  If and when you can enter the info that allows a successful boot, then, without rebooting, run sudo update-grub (and hope for the best!).

If you don't like the look of that, and if you haven't customized your ubuntu install much yet (which, since you can't get at it, is probably the case? :( ), remember that you could just reinstall.  You'll then be installing it second, after Windows, and grub should find both your existing Windows and the new ubuntu.

---

### Post by mr clark25 on 2010-08-27
if you wanted me to, i could probably make a simple bash script that would ask you a couple questions and then do everything else.

---

### Post by MintPaw on 2010-08-27
Yeah, I'll probably just re-install. I did have flash CS5 and all that jazz installed and it took me a while to figure out. Oh well.

---

### Post by mr clark25 on 2010-08-28
if you havent already re-installed, it really wouldnt be that hard for me to make the script. i plan to make it sometime anyway,(to post on my website) so i might as well make it now.

---

