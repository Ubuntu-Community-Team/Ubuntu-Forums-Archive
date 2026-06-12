---
title: "Re-Installing windows in dual-boot with ubuntu"
date: 2009-09-19
forum: General Help
---

### Post by daniel_gv93 on 2009-09-19
I have windows and ubuntu in a dual boot installed in my machine.
Windows got all messed up and I want to format and reinstall windows, but only that partition(without touching the ubuntu one)
I'm afraid that if I use the Gateway recovery CD to install windows it will erase my ubuntu partition as well.
Please, any help will be appreciated.:)

---

### Post by u'b'u'n't'u on 2009-09-19
I had a similar problem with my old gateway machine.  the gteway disc's purpose it to return it to the factory condition. i lost an installation of ubuntu by trying to "repair" the xp.  

if you have an official non-gateway xp cd, you can wipe out the windows partition, select that partition in the xp install and install it there.  Once you do this, your xp installation will boot, hiding your ubuntu installation, but don't worry, you can retrieve it by reinstalling GRUB. here is a little tutorial on how to do that:

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

If this doesnt work, or you need help just email me at stopspudabuse (at) aol(dot)com


happy computing and good luck!

your friend,
u'b'u'n't'u

---

### Post by solidblu on 2009-09-19
Yup. Aslong as you can get an OEM copy of Windows XP as long as it is the same type (Home,Pro) you can use the OEM cd key on the side of your PC to do the install.


Not all the drivers will be there, but that is just something you'll have to work through,  (maybe by dumping them on the windows partition via Ubuntu.

---

### Post by u'b'u'n't'u on 2009-09-19
if you don't have a retail/oem xp cd you are out of luck ): but theres always thepiratebay.com, besides, you already own an xp cd, theoretically giving you rights to download it. (at least in my opinion)

(if you want to go the more legal route, heres an alternative only 90 bucks [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2552182&CatId=672](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2552182&CatId=672))

---

### Post by yanceypd on 2009-09-19
You might try to use Clonezillato save the Ubuntu partition .  Reinstall after restoration.:)

---

### Post by pcjunkie on 2009-09-20
The drivers for the system will be contained in a folder. Even slipstreamed OEM installers keep the drivers elsewhere.

I would download something like XP lite myself. Less junk - more grunt.

---

### Post by Roasted on 2009-09-20
> **yanceypd said:**
> You might try to use Clonezillato save the Ubuntu partition .  Reinstall after restoration.:)

+1 for that. Clonezilla LiveCD is a great way to back up installs.

A while ago I was installing 9.04 when it came out and it failed due to my HDD beginning to crap out. I deleted Ubuntu and used Clonezilla to back up Vista. Got my new drive in, plopped Vista down, installed Ubuntu, was back in business in no time.

---

### Post by u'b'u'n't'u on 2009-09-20
yes i forgot about clonezilla. that is just what you need.

---

### Post by navneeth on 2009-10-13
Hello, everyone. I'm in a similar situation as the OP was.

However, I have two hard-disks. The master contains the Windows installation and the slave contains an NTFS partition containing important stuff while the rest of it is used for the Linux installation w/ swap.

```
Disk /dev/sda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32f97215

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/sda2            1021        2482    11743515    f  W95 Ext'd (LBA)
/dev/sda5            1021        1657     5116671    b  W95 FAT32
/dev/sda6            1658        2482     6626781    b  W95 FAT32

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x851f851f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1602    12868033+   7  HPFS/NTFS
/dev/sdb2            1603        4865    26210047+   5  Extended
/dev/sdb5            1603        4724    25077433+  83  Linux
/dev/sdb6            4725        4865     1132551   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb5298200

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

```

SDC1 is just an external hard-drive.

I, too, would like reinstall Windows XP. I came across this [[COLOR="Blue"][COLOR="Blue"]set of instructions[/COLOR][/COLOR]](http://www.stoltenow.com/archives/2006/11/reinstalling_wi.html) on how to save the MBR before performing the installation. It's been nearly three years since that was posted. Is it still an effective method? Or have there been better? Any other precautions that I should take (apart from backing my data up)? I have the SystemRescue LiveCD at hand to restore the original MBR.

Any help would be appreciated.

---

