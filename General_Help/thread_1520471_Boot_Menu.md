---
title: "Boot Menu"
date: 2010-06-29
forum: General Help
---

### Post by msirna on 2010-06-29
I just wanted to try Ubuntu for something different.  I had an extra hard drive laying around the house so I decided that I would try Ubuntu on that.  You see even though you have the option of trying it on the cd, I wanted to full experience.  My family uses Windows and with Ubuntu on a seperate hard drive in the same computer, now there is a silly boot menu when you restart and I don't want that especially with my family.  If I use the built in BIOS boot menu, I can select the other hard drive with Windows on it, but it still takes me to the Ubuntu boot menu.  I tried disconnecting the hard drive with Ubuntu on it, but it came up with a error saying that the device did not exist.  I then reconnected the drive and wiped it, hoping that the problem would go away.  For now, I'm going to reinstall Ubuntu on the other hard drive, just to get my computer working again.  I **_need_** to get my computer back to it's normal Windows working self WITHOUT the silly Ubuntu boot menu. 


Any help is greatly appreciated.

Thanks

---

### Post by GreenN00b on 2010-06-29
Boot into windows from your windows harddrive.
Run the command
```
fdisk /mbr
```
this will rewrite the master boot record of your hard drive, removing grub.
More details about the command [here]("http://support.microsoft.com/kb/69013")

You will be probably able to boot ubuntu when selecting other hard drive from bios.
Next time if you do not want this to happen do not install grub on the mbr of primary hard drive, I think this is an option in the ubuntu installer.

---

### Post by ajgreeny on 2010-06-29
> **GreenN00b said:**
> Boot into windows from your windows harddrive.
Run the command
```
fdisk /mbr
```this will rewrite the master boot record of your hard drive, removing grub.
More details about the command [here]("http://support.microsoft.com/kb/69013")

You will be probably able to boot ubuntu when selecting other hard drive from bios.
Next time if you do not want this to happen do not install grub on the mbr of primary hard drive, I think this is an option in the ubuntu installer.
I don't think the OP can boot to anything; that's the current problem.
Firstly, if you need to, restore the windows MBR with your windows install disk.  If you do not have a proper windows disk you will need to search a bit further, and note that the details vary with windows version, so you need to search for your own windows MBR version.

Having got windows running again, install ubuntu again, but this time when you are offered the final page option to continue, click on the Advanced button (see screenshot) and choose the disk on which ubuntu is installed, probably /dev/sdb, but do not add a partition number eg not /dev/sdb1.  Grub will now be put on the Ubuntu disk and the windows MBR will be left untouched.  Now you can choose the disk to boot to when you switch on by hitting the appropriate key, and if you choose disk1 it will go to windows, disk2 will go to ubuntu.

I hope that helps.

---

### Post by GreenN00b on 2010-07-06
The OP said > For now, I'm going to reinstall Ubuntu on the other hard drive, just to get my computer working again., my comment was based on that.

---

