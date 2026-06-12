---
title: "Resizing Ubuntu Partition"
date: 2009-08-10
forum: General Help
---

### Post by tanusgreystar on 2009-08-10
I gave my Ubuntu partition way too much space, and I would like to resize it to reclaim some space to use for data (mp3s, etc) and convert it to ntfs. Right now I'm running Ubuntu with XP dual boot and would like to be able to triple boot Win Vista or Win7. So I need space. My hdd is 750gb and I gave Ubuntu half of it thinking I could easily resize if needed, but I tried to resize it using Acronis in Windows, which wouldn't do anything to ext3 file system and Partitioner in Ubuntu won't work either. What do I need to do? Thanks.

---

### Post by stlsaint on 2009-08-10
you need to boot to a livecd like maybe the cd you used to install ubuntu and use gparted to resize  your partition.

---

### Post by Post Monkeh on 2009-08-10
> **stlsaint said:**
> you need to boot to a livecd like maybe the cd you used to install ubuntu and use gparted to resize  your partition.

what he said.

partition editor on the livecd would be your best bet.

---

### Post by tanusgreystar on 2009-08-11
That worked perfectly. Thanks!:guitar:

---

### Post by tanusgreystar on 2009-08-11
Now any idea on how to install Win7 when I already have XP and Ubuntu? Do I need to make changes to grub and/or winboot or boot.ini??

---

### Post by hibliss on 2009-08-11
You just install it on any empty partition that you created in gparted.

After the install Windows 7 bootloader will overwrite grub in the MBR, and this can be fixed using a LiveCD.

---

### Post by tanusgreystar on 2009-08-11
Ok I'm having issues here. I went to load Win7 and it installs, but then it goes to reboot and Grub is unchanged, so there's no Win7 on the menu. I edited grub and added win7 to the menu but I get a message saying no such device or something like that. I've tried changing the partition number for the win7 partition but I can't figure out which one it is. Ubuntu is (0,5) and the win7 partition comes after that one, so I've tried (0,6), (0,7), and (0,8). I can't finish installing win7 until I can boot into that partition. What am I supposed to do?

---

### Post by michy99 on 2009-08-11
When Grub comes up, choose XP, Maybe you will get a bootloader that let's you choose between XP and 7. Might work, might not.

---

### Post by hibliss on 2009-08-11
Can you post the results of:

```
sudo fdisk -l
```

I am wondering how your partitions are setup.

---

### Post by tanusgreystar on 2009-08-11
> **michy99 said:**
> When Grub comes up, choose XP, Maybe you will get a bootloader that let's you choose between XP and 7. Might work, might not.

nope:confused:

---

### Post by tanusgreystar on 2009-08-11
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ba01ba0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6346    50974213+   7  HPFS/NTFS
/dev/sda2            6347       91201   681597787+   5  Extended
/dev/sda5            6347       45509   314576766    7  HPFS/NTFS
/dev/sda6           45510       55236    78132096   83  Linux
/dev/sda7           55237       89972   279014400    7  HPFS/NTFS
/dev/sda8           89973       91201     9871911   82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x078bcbb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24792   199141708+   7  HPFS/NTFS

---

### Post by tanusgreystar on 2009-08-11
sda7 is win7 partition

---

### Post by hibliss on 2009-08-11
THIS may sound like a strange way to do this, but you can overwrite Grub with XP's bootloader if you have the disc, just fire it up and FixMBR. This will not affect your partitions or installed Operating Systems, but you will not longer be able to access Grub or Ubuntu. After that, install Win 7 as usual, then take the step to restore Grub and create entries for each OS.

---

### Post by tanusgreystar on 2009-08-12
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
chainloader	+1
title		Microsoft Windows 7
root		(hd0,6)
makeactive
chainloader	+1


this is what I put in grub. Is this right??

---

### Post by hibliss on 2009-08-12
Here is the thing, even if you get things right in Grub, after the Windows install, Grub will be gone and you will be starting from scratch with it.

---

### Post by tanusgreystar on 2009-08-12
ok I'll try it

---

### Post by madhavhmk on 2009-08-12
have you tried editing /boot/grub/menu.lst  ?

try setting the partition near win7 as (hd0,6) , reboot

---

### Post by tanusgreystar on 2009-08-12
Yeah I did that, but not successful. I tried (0,6) as well as other partitions. I did repair windows mbr so there's no grub right now. I'm going to load win7 then replace grub and see what happens. Thanks.

---

### Post by tanusgreystar on 2009-08-12
Well the issue seems to be with Win7. I repaired the mbr in windows xp then installed win7 and when it goes to reboot the only available option is xp. I wonder how to fix that.

---

### Post by tanusgreystar on 2009-08-12
Ok this is weird. I loaded the ubuntu cd and chose to boot from hdd and I got win7 as the only option! It continued to install, but when it went to reboot I got xp again. So somehow I need to get everything together in one menu. Hmmm...

---

### Post by hibliss on 2009-08-12
For some reason the Win 7 bootloader is not overwriting the MBR, maybe due to the way the partition table is setup. I really don't know the answer, as Windows generally has no issue hijacking the MBR and locking out every other non MS OS.

---

### Post by oldfred on 2009-08-12
I found this I think on Herman's site:
I don't have makeactive on Vista's option as it makes the option unbootable.

title        Windows 7 Ultimate, chainloader (on /dev/sda1)
rootnoverify    (hd0,0)
savedefault
chainloader +1


Your entry should be (hd0,6) as you have in your current menu.lst. The other issue is that Windows should be on a primary partition. It works a whole lot better. Somewhere someone said they had it working in a extended partition, but I do not remember what they did.

---

### Post by Post Monkeh on 2009-08-12
> **hibliss said:**
> Here is the thing, even if you get things right in Grub, after the Windows install, Grub will be gone and you will be starting from scratch with it.

normally the grub menu isn't affected, it just overwrites the mbr.

once you follow one of the guides for restoring grub, i've always found all my grub settings to be fine.

fwiw, bu dad installed the win7 release candidate on his pc and it totally screwed up every time he tried it and wouldn't let him boot into xp. he ended up just deleting it and restoring the xp boot loader.

---

### Post by tanusgreystar on 2009-08-13
I ended up reinstalling ubuntu, and when it rebooted, Win7 was on the grub menu (as Vista loader). So I'm able to boot into 7. Seems very unstable. It has run chkdsk 3 times because of corruption. I'm only going to put up with that for so long! Thanks for the help guys!:guitar:

---

