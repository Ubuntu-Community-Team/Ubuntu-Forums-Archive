---
title: "Encrypted disk has crashed, in serious need of help"
date: 2011-07-31
forum: General Help
---

### Post by ericus on 2011-07-31
I'm running full disk encryption, installed from the alternative CD.

Yesterday I was browsing the internet, when firefox suddenly crasched, and after that the screen went black. Could not drop out to a terminal or do anything, so I rebooted the computer.

System boots up, asks me to enter my passphrase. After entering that it gives me "sda5_crypt setup successfully" as normal. Then, after a couple of seconds it drops to a busybox-shell, which tells me "no init found, Try passing init=bootarg".

Googled that problem, and found [this](http://ubuntuforums.org/archive/index.php/t-1200023.html) thread. Booted up my computer with a live USB. Unfortunately, the solution for encrypted disks posted in the thread does not work. I can successfully (?) open the disk with ```
sudo cryptsetup luksOpen /dev/sda5 krypto-sysroot
```, but running sudo pvscan after doing that gives me I/O errors.

System > Administration > Disk Utility tells me that the disk has bad blocks, and when I tried to fix them it just wont work.

When running fdisk -l after entering my passphrase it tells me that "Disk /dev/dm-0 doesn't contain a valid partition table".

Unable to mount the disk, but still fdisk -l lists it. I've spent 15+ hours of desperate googling and testing possible solutions, but nothing will work.

I will not accept the fact that the disk might be physically damaged before I've tried every possible solution. I have some seriously irreplaceable data on that disk (thank God that I've at least got backups on all my pictures). If anyone would be able to help me I'd be forever grateful.

Just ask if you need terminal outputs or something, I'm on my netbook right now.

Best regards,
Eric

---

### Post by AlphaLexman on 2011-07-31
[This link]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") is for recovery on ~/Private directory, but may offer some help!

---

### Post by ericus on 2011-07-31
> **AlphaLexman said:**
> [This link]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") is for recovery on ~/Private directory, but may offer some help!

No, that does not apply for my problem, but thank you anyway! :)

---

### Post by ericus on 2011-07-31
Forgot to mention, sometimes the disk does not show up in BIOS and gives I/O errors when unlocked.. I am willing to offer 50€ to someone with a working solution. If this is against the forum rules, please remove this post. But I am desperate.

---

### Post by ericus on 2011-08-01
Anyone, please? :(

---

### Post by aeiah on 2011-08-01
i tend to avoid full disk encryption for this reason (i just shove my important stuff in a truecrypt container)

only thing i can suggest is that, if possible, mirror the whole disk using dd (or ddrescue) so you can poke around and attempt repairs without running the risk of making things worse.

perhaps look into tools that the ubuntu rescue remix or ultimate boot cd provides.

---

### Post by westie457 on 2011-08-01
> **ericus said:**
> Forgot to mention, sometimes the disk does not show up in BIOS and gives I/O errors when unlocked.. I am willing to offer 50€ to someone with a working solution. If this is against the forum rules, please remove this post. But I am desperate.

Hi bad news here. Your hard drive is dying. Stop using it before it fails completely. You did not state whether this is happening to a laptop or a desktop. Get another hard drive either internal or external your choice. However it must be at least the same capacity of the dying one.

Connect it to the box and boot into a LiveCD/USB. From the live desktop open a terminal and run ```
dd if=/dev/sda of=/dev/sdb
```
Here I have assumed that sda is the old drive and sdb is the new.one. Check first with ```
fdisk -l
``` or using Gparted for a graphical view.

The first command will do a byte for byte copy of the old to the new. It might not help clear the problem with the encryption issue but at least you will now have a back up of all your files.

---

### Post by ericus on 2011-08-02
AAAH! YES! I finally solved it! :D

What I did was make a clean live USB again, to get rid of all the data I had saved on it and start fresh. Then I booted up from it, installed cryptsetup and lvm2.

```
cryptsetup luksOpen -v /dev/sda5 sda5_crypt
```
..which worked well, as always. Wasn't hoping for any further progress at this time.

Then, I tried to list volume groups, but that failed on me again:
```
lvdisplay
```

Thought I was f*cked, but decided to try System > Administration > Disk Utility. Saw the disk there, clicked "activate volume group" or something like that. Finally some progress.

After that I tried to mount it:
```
mount /dev/mapper/sysroot /mnt
```
..AND IT WORKED!

The guide I was following (and have tried serveral times before without succes) was this one: [http://blog.bitengine.ca/?p=72](http://blog.bitengine.ca/?p=72)

As you can see, I skipped a lot of steps, and everything worked out. I'm right now doing backups of my most important files, and a new disk is on it's way.

---

