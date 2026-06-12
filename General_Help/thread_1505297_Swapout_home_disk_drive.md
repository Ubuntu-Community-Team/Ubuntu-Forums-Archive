---
title: "Swapout /home disk drive"
date: 2010-06-09
forum: General Help
---

### Post by gandalf2000 on 2010-06-09
I have my /home on a separate drive to my system drive but my /home drive is failing (after only 210 days, it's going back).  So I have a new drive to replace it and all my stuff has been copied to a usb drive to ;oad when it is done.  Can I just remove the old /home disk and put the new one in it's slot or will this kill the system?  If so, how can I get this done?

---

### Post by lindsay7 on 2010-06-09
If you have the root directory on /  one drive and /home on a separate drive.  You should be able to copy over the files to the new drive. I would think that you will need to set up the new drive as /home.  I am not sure how you do this as I have always set up the /home drive from the Ubuntu install disk. You may be able to do this with the install disk without installing the system on / but I have never done this.

---

### Post by srs5694 on 2010-06-09
Chances are you'll need to do one of two things (in broad outline):


[list]
[*]Clone the original disk to the new one using a low-level utility that copies the UUID, then replace the old disk with the new one. When you reboot, Ubuntu will probably see the new disk as if it were the old one and everything will work.
[*]Prepare the new disk (partition it and create filesystem(s) on the partition(s)), then copy the old files onto the new partition(s), then edit /etc/fstab to change the UUID from the old /home to whatever the UUID is on the new /home. When you reboot with the old disk disconnected and the new one installed, everything should work.
[/list]


Both of these methods assume that your system is configured to identify your /home partition by UUID, as in:

```

UUID=580d3322-2ff8-4692-a964-be996c2e9929       /home    ext3           noatime        0 2

```

Ubuntu uses this method by default. If instead of the UUID method your system uses a device ID (such as /dev/sdb1), you probably won't need to change it if you do a low-level cloning operation, and you might or might not need to change it if you manually create new partition(s) on the new disk, depending on whether the new partition(s) match what's on the old disk.

If you need to ask more questions, I suggest you post your /etc/fstab file, or at least the entry for /home from that file. Doing so will replace assumptions with certainties.

---

