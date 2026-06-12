---
title: "Corrupt File System, How to Recover?"
date: 2010-01-04
forum: General Help
---

### Post by ToddFisher on 2010-01-04
Hello,

I have an Acer Aspire One running NBR 9.10.  A few days ago it "went wonky", wouldn't boot and would just seem to start and then shut off before getting to the logon screen.  I managed to boot from a USB stick and run check and fix in Gparted.  It found a slew of errors in the file system.  Unfortunately, it still won't boot, now it just hangs.  I assume some of boot files were damaged.  

Now I have two problems:

1.  Is there a way to repair the damage?  Or just wipe the disk and start over?

2.  I need to get my e-mail off of the hard drive.  I can mount the drive after booting from a USB stick, but the thunderbird directory is locked.  Is there a way around this?

Thanks!

---

### Post by cariboo on 2010-01-04
Boot from your usb device, then open a terminal, and type:

```
sudo fsck -a /dev/sda
```

substitute your device label for the one in the example above. If you need to copy files from the drive, use nautilus as root. Press Alt-F2 and type:

```
gksudo nautilus
```

the above command will open the file manger in root mode and allow you to access the files you need.

---

### Post by ToddFisher on 2010-01-04
Thanks!  That works, I copied all the e-mails and data off.

Now....about repairing the damage.  That scan says the disk is fine, but I still can't get it to boot.  Gets to the login screen, and then hangs.

---

