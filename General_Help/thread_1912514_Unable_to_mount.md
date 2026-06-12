---
title: "Unable to mount"
date: 2012-01-20
forum: General Help
---

### Post by popejeremy on 2012-01-20
I plug in my external hard drive (named El Baz) into my laptop. I open my home folder window, and El Baz shows up in the list under Devices. I select El Baz and I get a popup window saying "Unable to mount El Baz. Not Authorized."

What can I do?

---

### Post by carranty on 2012-01-20
> **popejeremy said:**
> I plug in my external hard drive (named El Baz) into my laptop. I open my home folder window, and El Baz shows up in the list under Devices. I select El Baz and I get a popup window saying "Unable to mount El Baz. Not Authorized."

What can I do?

What are you using to open your home folder?  I don't have a 'Devices' menu.....

Anyway, since I don't know what OS you're running, I'll tell you how to mount using to terminal (this should work for any version of Ubuntu/Kubuntu etc).  To mount you'll first need to create a mount point, open a terminal and type

```
sudo mkdir /mnt/El_Baz
```before you can mount it, you'll need to know its location, type

```
df -h
```in a terminal, look at the left hand column, this is the property you need, you should be able to figure out which row corresponds to your hard drive by looking at the 'Size' column (it'll be one of the ones that begins with /dev).  I have an external drive on /dev/sdb1

Then simply type the below in a terminal

```
sudo mount /dev/sdb1 /mnt/El_Baz
```where you should replace /dev/sdb1 with the line you found in the previous step.

Now you can close the terminal and load up whatever file browser you normally use, the hard drives contents can be found in the /mnt/El_Bak directory

---

### Post by popejeremy on 2012-01-20
By "Devices" I just mean the list in the left-hand side of the nautilus window.

Anyway, I tried what you said. Here's what happens.

```
jeremy@Stanton:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             228G  208G  8.2G  97% /
udev                  996M  4.0K  996M   1% /dev
tmpfs                 401M  980K  400M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                 1003M  936K 1002M   1% /run/shm
/home/jeremy/.Private
                      228G  208G  8.2G  97% /home/jeremy
df: `/root/.gvfs': Permission denied

```

I don't see the hard drive anywhere.

---

### Post by mikaelcrocker on 2012-01-20
open up the fstab file and mount it there.  You could use dh to dertmine the requirements for it, but that will mount it everytime at start up.

---

### Post by carranty on 2012-01-21
> **popejeremy said:**
> By "Devices" I just mean the list in the left-hand side of the nautilus window.

Anyway, I tried what you said. Here's what happens.

```
jeremy@Stanton:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             228G  208G  8.2G  97% /
udev                  996M  4.0K  996M   1% /dev
tmpfs                 401M  980K  400M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                 1003M  936K 1002M   1% /run/shm
/home/jeremy/.Private
                      228G  208G  8.2G  97% /home/jeremy
df: `/root/.gvfs': Permission denied

```I don't see the hard drive anywhere.

Sorry, the df command will only list the currently mounted drives - my mistake, it was a long day yesterday.  You could just try trial and error, its probably /dev/sdb or /dev/sdb1 or /dev/sdc or /dev/sdc1.  To find out for sure follow the below steps

1) unplug the drive
2) in a terminal write

```
tail -f /var/log/messages
```This will bring up a continously updating log file.

3) Plug in your external hard drive and some new messages will appear. On my system the below appeared

```
Jan 21 11:36:11 carranty-desktop kernel: [ 1531.372023] usb 1-4: new high speed USB device using ehci_hcd and address 5
Jan 21 11:36:11 carranty-desktop kernel: [ 1531.505808] usb 1-4: configuration #1 chosen from 1 choice
Jan 21 11:36:11 carranty-desktop kernel: [ 1531.566961] Initializing USB Mass Storage driver...
Jan 21 11:36:11 carranty-desktop kernel: [ 1531.567105] scsi4 : SCSI emulation for USB Mass Storage devices
Jan 21 11:36:11 carranty-desktop kernel: [ 1531.567526] usbcore: registered new interface driver usb-storage
Jan 21 11:36:11 carranty-desktop kernel: [ 1531.567530] USB Mass Storage support registered.
Jan 21 11:36:17 carranty-desktop kernel: [ 1537.107769] scsi 4:0:0:0: Direct-Access     BUFFALO  External HDD          PQ: 0 ANSI: 2 CCS
Jan 21 11:36:17 carranty-desktop kernel: [ 1537.108496] sd 4:0:0:0: Attached scsi generic sg3 type 0
Jan 21 11:36:17 carranty-desktop kernel: [ 1537.109795] sd 4:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jan 21 11:36:17 carranty-desktop kernel: [ 1537.111732] sd 4:0:0:0: [sdc] Write Protect is off
**Jan 21 11:36:17 carranty-desktop kernel: [ 1537.113993]  sdc: sdc1**
Jan 21 11:36:17 carranty-desktop kernel: [ 1537.134109] sd 4:0:0:0: [sdc] Attached SCSI disk
```The bold line is the line of interest, it's telling me the hard drive is located at /dev/sdc1.  Use whatever yours says in the last command of my original post and it should mount.

If you're still not sure, post the output of the 'tail -f /var/log/messages' to this thread (right after you plug in the drive) and I'll post back the exact command you need to mount the drive.

EDIT : If you would like your computer to mount the drive automatically each time you boot up, you can modify your fstab file, however you'll still need to do the above the first time in order to get the details of the drive (as far as I know at least).

---

### Post by popejeremy on 2012-01-22
So, I just added a line to my fstab. It works for now, but this I is a hack. I'd rather that it works the way it's supposed to.

---

