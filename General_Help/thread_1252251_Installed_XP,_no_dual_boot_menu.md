---
title: "Installed XP, no dual boot menu"
date: 2009-08-28
forum: General Help
---

### Post by endersbean3k1 on 2009-08-28
Hi guys, I just installed XP on a previously unpartitioned space on my hard drive. Now when I boot the computer I don't get a boot menu like I was expecting, it just goes straight to windows. I'm on a live CD right now and everything seems ok with the old Linux partition, I just can't boot to it.

Here's sudo fdisk -l

```
Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00003295

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24315   195310206   83  Linux
/dev/sda2           24316       25288     7815622+   5  Extended
/dev/sda3   *       25289       36480    89899740    7  HPFS/NTFS
/dev/sda5           24316       25288     7815591   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00028818

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

```

If I just reformat the 92GB windows partition, will I get my Ubuntu back? Is there an easy way to get dual boot? I saw something during the windows partition about a setting, but I wasn't able to locate the info.

Sorry if something I'm asking for is easy to find, I'll admit I only spent a couple minutes searching as I must leave now.

Thanks for the help, you guys are always great.

---

### Post by denver on 2009-08-28
When you installed Windows, your MBR (Master boot record) was overwritten. The master boot record is a small portion on your hard drive that tells your computer where to find the operating system. This is were you usually install GRUB to take over the process of loading your OS.

To reinstall it you must boot up any Ubuntu live CD and in a termina, type in the following:

```
sudo grub
```

You will be prezented with something like this:

```
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>
```

What you need to do now is find out where your boot partition is:

```
grub> find /grub/stage1
 (hd0,5)
[code]

This will show you where your boot partition is (in my case its hd0,5). If you do not have a separate /boot partition, the above command will say:

[code]Error 15: File not found
```

Don't panik, just type:

```
grub> find /boot/grub/stage1
```

after that just run the following command one after another:

```
root (hd0,5)
setup (hd0)

```

You should see something like this:

```
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/grub/stage2 /grub/menu
.lst"... succeeded
Done.
```

Reboot and you should see a GRUB menu again.

NOTE: Replace hd0,5 with whatever output you get from the find command.

---

### Post by endersbean3k1 on 2009-08-28
Sweet guide, worked like a charm.

How do I install XP WITH the dual boot now? Looking it up, I figure it'll be all over the place as this is probably the #1 thing many newcomers need. Thanks a bunch for the help though.

Edit: Ok, that didn't take long. I see that this IS the procedure to install XP second and get the dual boot. I rebooted to double-check that there wasn't a way to get to windows. Definitely NOT there. What gives?

---

### Post by Vince N on 2009-08-28
Try adding this to
/boot/grub/menu.lst after your Ubuntu entries.  Change (hd0,0) to what ever actualy has your windows partition on it.

```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

```

---

### Post by endersbean3k1 on 2009-08-29
Thanks, worked great :)

Now to get XP working... I just feel the need to say that my internet on ubuntu worked out of the box, and I can't get jack to work on XP.

But that's not really relevant, thanks for the fast responses guys.

---

