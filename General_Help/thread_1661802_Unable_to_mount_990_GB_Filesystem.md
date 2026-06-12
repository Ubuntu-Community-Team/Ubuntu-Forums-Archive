---
title: "Unable to mount 990 GB Filesystem"
date: 2011-01-07
forum: General Help
---

### Post by stuwoody007 on 2011-01-07
I have had a system crash and have no idea why - I have booted up through the cd and are runnign off that but i need to know how to get the information off the hard drive before I attemp to format and start again.

Any thoughts?

Error msg:

Unable to mount 990 GB Filesystem
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

---

### Post by Ghost_Mazal on 2011-01-07
Have no thoughts on that error. I assume you want to copy your data to an external device.

You can also try a parted magic bootable cd. That is also handy for mounting HDD's and copying data.

---

### Post by stuwoody007 on 2011-01-07
I have had a system crash and have no idea why - I have booted up  through the cd and are runnign off that but i need to know how to get  the information off the hard drive before I attemp to format and start  again.

Any thoughts?

Error msg:

Unable to mount 990 GB Filesystem
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

---

### Post by stuwoody007 on 2011-01-07
the problem is I dont know where the data is stored.

Where is it normally stored - everything is save under the file system download pictures etc??

---

### Post by Ghost_Mazal on 2011-01-07
By default all your pictures and docs etc are stored in the /home folder.

You will see /home/username

Inside that is all your default locations for docs , music , pictures downloads etc.

If you never told it to save somewhere else you should find it there.

---

### Post by stuwoody007 on 2011-01-07
as i am booting through a CD the home folder is different and that error comed up everytime i try to access the HD

---

### Post by Ghost_Mazal on 2011-01-07
I think you are accessing the cd's filesystem. You need to find your hdd and that might be under /media if the cd mounted it automatically. If it is not there then someone more knowledgeable will need to help you with manual mounting of your HDD. (assuming off course your HDD isn't faulty)

---

### Post by stuwoody007 on 2011-01-07
thanks mate for tryin - looks like others have had this problem before but cannot find a solution

---

### Post by Ghost_Mazal on 2011-01-07
If I were you I would at least try something like parted magic boot cd as well. But with a broken system , how would you dl and burn it is the problem.

---

### Post by dino99 on 2011-01-07
try booting (cold boot) in recovery mode, then choose "repair packages" then "continue normal boot"

---

### Post by s.fox on 2011-01-07
Please do not create duplicate threads. Thank you.

Threads  Merged.

---

### Post by stuwoody007 on 2011-01-07
when i boot again it stops at INITRAMFS and goes no further

Missing modules (cat/pooc/modules/isdev)

alert! /dev/disk/by-uuid/12bfoo7d-3bab-48et-b9ia-6abc68ab3223 does not exist

thoughts?

---

### Post by stuwoody007 on 2011-01-07
do not mean to duplicate threads but when i reboot i cannot find the threads i have posted

How do i find previous threads i have posted?

---

### Post by Elfy on 2011-01-07
> **stuwoody007 said:**
> do not mean to duplicate threads but when i reboot i cannot find the threads i have posted

How do i find previous threads i have posted?

Search at the very top - dropdown menu - your threads or posts are 2 of the options.

---

### Post by Dave1701 on 2011-01-08
I had the same thing happen to me (with a 500 GB Primary Drive and a 1.5TB Slave).  Both of the drives refused to mount and the system started with initramfs and Busybox.  Even the live cd of Lucid would not let me mount either drive. I booted a live CD of RIPLinux  and scanned the drives.    They also refused to mount with the live cd of RIPLinux.  For reasons unknown (after several reboots and scans with Testdrv), the drives finally mounted.  No data lost and the system is working again.  Really weird problem!  Hope it resolves itself.

---

### Post by stuwoody007 on 2011-01-10
Still having the same problem - my issue is that I was in the progress of transferring my photos - have installed ubuntu on another hdd but still cannon mount or access drive - any help would be so appreciated as its 10 years of photos i cannot replace

---

