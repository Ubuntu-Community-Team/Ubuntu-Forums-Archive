---
title: "Grub Rescue: No Such Device"
date: 2011-01-24
forum: General Help
---

### Post by CST10 on 2011-01-24
[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-ash1/hs774.ash1/166420_494471623578_669203578_6196011_152064_n.jpg[/IMG]

The only solutions I've seen is to load an install disc of either windows or ubuntu, which I can't do since I can't press F2 or F12 to get to the bios menu to select a different place to boot from. What commands do I need to give it to get it to boot windows, at least.

---

### Post by wilee-nilee on 2011-01-24
It will help if you mention the type of install, eg Wubi, or a partitioned dual boot from a booted Ubuntu cd.

Were you in the past able to use the f2 and f12 keys and which did what? Are you also trying those keys correctly, on powering on immediately, and depressing repeatedly.

If this is a wubi we can fix the MS bootloader from a live Ubuntu cd, the same can be done for a dual booted Ubuntu install.

---

### Post by CST10 on 2011-01-24
> **wilee-nilee said:**
> It will help if you mention the type of install, eg Wubi, or a partitioned dual boot from a booted Ubuntu cd.

Were you in the past able to use the f2 and f12 keys and which did what? Are you also trying those keys correctly, on powering on immediately, and depressing repeatedly.

If this is a wubi we can fix the MS bootloader from a live Ubuntu cd, the same can be done for a dual booted Ubuntu install.

The keys are dead, can't explain it, it happened after updating from win vista to 7. Half of my F-Keys and the numbers 4 and 6 don't work. F2 enters the Bios menu, and F12 selects what drive to boot from. So even if a bootable CD or thumb drive is in, it won't select them. It just goes right to trying to boot ubuntu, no OS selection menu like normal.

Wubi I guess, installed in windows. Latest version of Ubuntu. It's where I downloaded it in windows, it installs inside windows.. basically.

Installed Ubuntu, it updated, asked to update something related to the Grub so I said OK. It restarted to the regular OS selection menu, I hit Ubuntu and got this. Restarted, os selection came up again, selected Ubuntu thinking it was just a one-time error, and got right back to this. And now it just defaults to trying ubuntu.

---

### Post by wilee-nilee on 2011-01-24
> **CST10 said:**
> The keys are dead, can't explain it, it happened after updating from win vista to 7. Half of my F-Keys and the numbers 4 and 6 don't work. F2 enters the Bios menu, and F12 selects what drive to boot from. So even if a bootable CD or thumb drive is in, it won't select them. It just goes right to trying to boot ubuntu, no OS selection menu like normal.

Wubi I guess, installed in windows. Latest version of Ubuntu. It's where I downloaded it in windows, it installs inside windows.. basically.

Installed Ubuntu, it updated, asked to update something related to the Grub so I said OK. It restarted to the regular OS selection menu, I hit Ubuntu and got this. Restarted, os selection came up again, selected Ubuntu thinking it was just a one-time error, and got right back to this. And now it just defaults to trying ubuntu.

Okay, that is a good description.:) Have you tried another keyboard, personally I don't know of any other way of fixing this other then reloading the mbr, which would be done with a bootable disc.

---

### Post by CST10 on 2011-01-24
> **wilee-nilee said:**
> Okay, that is a good description.:) Have you tried another keyboard, personally I don't know of any other way of fixing this other then reloading the mbr, which would be done with a bootable disc.

Ha, been using laptops so long I forgot about using another keyboard... 

Got it to boot from a Ubuntu install CD, and it goes to Busy Box v1.15.3 with an error message.

```

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error
Can not amount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

```

---

### Post by wilee-nilee on 2011-01-24
So we don't know the Windows setup you have. What your missing is the MS bootloader, do you have a recovery disc or install disc for the windows OS. 

You may need to to burn another Ubuntu cd to get it to boot, it needs to be burned as a image, not data. You can also load the Ubuntu to a thumb with unetbootin as well.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Either bootable disc/thumb can be used to reload the mbr.

If you can get into a live Ubuntu desktop then you can use lilo to reload the mbr. Make sure your HD is being read as sda by running this command first. No partition numbers just the first three letters=sda, or sdb...etc
sudo fdisk -lu

Then here are the commands for loading lilo.
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by CST10 on 2011-01-24
> **wilee-nilee said:**
> So we don't know the Windows setup you have. What your missing is the MS bootloader, do you have a recovery disc or install disc for the windows OS. 

You may need to to burn another Ubuntu cd to get it to boot, it needs to be burned as a image, not data. You can also load the Ubuntu to a thumb with unetbootin as well.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Either bootable disc/thumb can be used to reload the mbr.

If you can get into a live Ubuntu desktop then you can use lilo to reload the mbr. Make sure your HD is being read as sda by running this command first. No partition numbers just the first three letters=sda, or sdb...etc
sudo fdisk -lu

Then here are the commands for loading lilo.
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

Success! Windows is booting. I'll report back after I try Ubuntu.

Do you have an idea what caused this problem?

---

### Post by wilee-nilee on 2011-01-24
> **CST10 said:**
> Success! Windows is booting. I'll report back after I try Ubuntu.

Do you have an idea what caused this problem?

You mentioned, a upgrade of grub in the wubi, here is a thread that gives you more information. 
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by CST10 on 2011-01-25
Thanks. Ubuntu is working perfectly as well. Thanks again for the help!

---

