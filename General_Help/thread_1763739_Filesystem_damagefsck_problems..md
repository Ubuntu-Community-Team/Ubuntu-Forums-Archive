---
title: "Filesystem damage/fsck problems."
date: 2011-05-20
forum: General Help
---

### Post by Eidolonz983 on 2011-05-20
So I had to force a reboot because of a freeze and when I booted back up it came to a black terminal screen where it said /dev/sda1 has file system errors which Im assuming is preventing Ubuntu from booting up. 

I dont remember the exact error messages, or how to print them, since Im posting from my USB boot. 

However, Ive read that I should do an fsck to try and repair. Ive made sure the partition is there with fdisk -l, and it shows, but  sudo fsck -y /dev/sda1 returns this: 

/dev/sda1: clean, 312137/15138816 files, 28752164/60525568 blocks


How do I get fsck to fix the errors that are preventing me from using my main install?

I am an ubuntu newbie, so I apologize if there's more I should have done up to this step.

UPDATE: Using the disk utility in Admin returns "filesystem is clean" yet my install will not boot up.

---

### Post by tgalati4 on 2011-05-20
Well, something else is preventing boot up.  Try hitting Alt-F1 during boot and watch the messages scroll by.

---

### Post by linuxinstalledfromhdd on 2011-05-20
You should run a disk check of your hard drive from a live bootable usb ubuntu if you can. See what the results look like. If you have a bad hard drive, it might cause this.

---

### Post by Eidolonz983 on 2011-05-21
I tried booting into safemode and kept getting I/O errors, so Im going to go with it being a dying hard drive.

Im going to copy as much as I can and just get a new drive and start over.

---

### Post by philinux on 2011-05-21
> **Eidolonz983 said:**
> I tried booting into safemode and kept getting I/O errors, so Im going to go with it being a dying hard drive.

Im going to copy as much as I can and just get a new drive and start over.

You could meanwhile check the drive from your usb stick.

System Admin>disk utility. Check the SMART data.

Also try this from usb.

```
sudo fsck -vy /dev/sda1
```

---

### Post by tgalati4 on 2011-05-21
If you are getting I/O wait messages in:

dmesg | more

Then it could be a loose cable or power connector.  That happened to me once.  I had a machine running for years (Dapper Drake) and the vibrations over time caused the power connector to loosen.  It caused the strangest errors--clean file system but random I/O waits--as the drive would randomly shut down.

Also check your power supply.  A bad 12VDC rail can cause similar problems as the motherboard runs on 5VDC but the hard disk needs 12VDC to keep spinning.

Use a volt meter to check between the black and yellow leads.  It should be no less than 11.75VDC.  If your power supply says "Bestec" be doubly suspicious.

---

