---
title: "Cannot access hard drive"
date: 2009-07-05
forum: General Help
---

### Post by TimSmith-Laing on 2009-07-05
Hi there, I'm new to Ubuntu, and so far think it could be great for me. BUT, now I've installed, I'm unable to view one of my two hard disks - the one with all my files on. Thanks to the tiny size of the default Windows partition I had originally, all my files are on what XP designated drive D. Search as I might, I can't find it anywhere. My shortcut to it also no longer works...

Can anyone help me out?

Thanks,

Tim

---

### Post by michy99 on 2009-07-05
Open a terminal, enter this command, and post the result here.```
sudo fdisk -l
```(That is l as in lion, not 1 as in 1,000)

---

### Post by phillw on 2009-07-05
[SIZE=3][FONT=Arial]Hi Tim,

If you click on 'Places' at the top of the screen (towards the left corner) - it will list all the drives it sees - My windows one appears as 53GB Media - just click on the name, and it should mount onto your desk-top for you.

If, like me, you want it to mount each time you boot Ubuntu then the easiest way is to install pySDM. Whilst there are instructions on this forum - as I am  writing this reply - the quickest link I could find that does exactly the same thing is 

[http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14](http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14)

Regards,

Phillw.

P.S. Welcome to Ubuntu :p
[/FONT][/SIZE]

---

### Post by TimSmith-Laing on 2009-07-05
Hi guys, thanks for this!

Michy, here's what I get in terminal:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb21432ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3648    29302528+   7  HPFS/NTFS
/dev/sda2            3649       19457   126985792+   f  W95 Ext'd (LBA)
/dev/sda5            3649       19457   126985761    7  HPFS/NTFS

---

### Post by michy99 on 2009-07-05
I don't see a linux partition at all. Did you install from windows using Wubi? Do you have two actual physical drives, or just one drive with several partitons?

---

### Post by TimSmith-Laing on 2009-07-05
Sorry michy, should have said. I installed through wubi and have one partitioned drive.

---

### Post by Nevart on 2009-07-05
Unless it is some sort of hardware problem or a fault in the OS, you may not have to go through all that trouble.

If you right-click on the "panel" area (in the blank space between the clock and the launch menus) you can select "Add to Panel".

In the list of things you can pick from, you'll find something called "Disk Mounter".

This lets you mount any drive (or partition) installed on the system.  The "C" drive does not get mounted automatically, probably because they assume you don't want to mess around with your Windows stuff (and it may be a security precaution).

To mount a drive, just left-click on its icon in the Disk Mounter panel utility and select "Mount".  Don't right-click, because that just brings up the context menu for the panel item and not for the disk.

Hope that is some help.  I had this problem myself and it took a bit of experimenting to find it.

Unmounting is via the same process.

---

### Post by michy99 on 2009-07-05
Well, that explains why there isn't a linux partition. I really don't know much about how wubi installs as I have never used it. I know it installs in a file on your windows partition instead of creating a new partition.

Now, about the problem, let me see if I understand what is going on. You can boot into Windows or Ubuntu with no problem, right? Does your D: disk show up in Windows, but not in Ubuntu, or does it no longer show in Windows either? If it is just in Ubuntu you don't see it, it is just a question of mounting it. If it doesn't show in Windows, there is something more serious going on.

---

### Post by TimSmith-Laing on 2009-07-05
Hi Nevart,

Thanks for that...I've done what you said but can't seem to bring up the utility. When I click or right-click on disk mounter I only get the currently mounted 'vaio' coming up and no option to mount another disk. Think this is going to take some experimenting....

Tim

---

### Post by TimSmith-Laing on 2009-07-05
Michy, certainly before booting into ubuntu D was accessible in windows. Would reboot into windows and check if ubuntu wasn't still busy updating right now. Will check as soon as the updates are finished.Till then I'll explore some more and get back to you.

Really appreciate your help!

Tim

---

### Post by michy99 on 2009-07-05
Ok, After you get done updating, boot into windows and make sure everything works from there like it should. I have to leave for church soon, but I will check back in this thread this afternoon when I get back. Maybe you will have it sorted out by then.

---

### Post by Nevart on 2009-07-05
Disk mounter should have come up in the panel with a bunch of disk icons (maybe two or three).  And you just need to left click to open a menu to mount the disk.  But if you don't see any disk icons, or if it only shows you disks that are already mounted, then you have a bigger issue going on there.

It's just a normal disk, right?  Not SATA or something?

---

### Post by TimSmith-Laing on 2009-07-05
Hm, it just comes up with the one disk, still, the 'vaio' volume. I'm just going to try PySDM and see if that brings anything up...

---

### Post by TimSmith-Laing on 2009-07-05
Ha! Don't know if I was being slow earlier or if automount has worked but having identified my D drive as sda5, I can now bring it up in the file browser. Brilliant! Problem solved. Thanks for all your help guys! Really, really appreciate it!

Tim

---

### Post by michy99 on 2009-07-05
Glad to hear you got it working. When I first read your post, I was afraid you might have installed Ubuntu over your data, but I didn't want to say so unless I was sure. Glad that wasn't the case.

---

