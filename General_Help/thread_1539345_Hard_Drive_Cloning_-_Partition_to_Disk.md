---
title: "Hard Drive Cloning - Partition to Disk"
date: 2010-07-26
forum: General Help
---

### Post by vttay03 on 2010-07-26
--I know hard drive cloning is a topic that's constantly discussed over and over but I need some insight.  I essentially have 3 hard drives in my computer:

1) /dev/sda - Windows (320 GB)
2) /dev/sdb - Currently empty (320 GB)
3) /dev/sdc - Ubuntu 10.04 and Slackware 13.0 (500 GB; each OS is 250 GB); uses Grub2 to control booting

Right now I'm using Grub2 to control booting and it's on the MBR of /dev/sdc.  I ultimately want to be in the following configuration:

1) /dev/sda - Windows (320 GB)
2) /dev/sdb - Ubuntu 10.04 (320 GB); uses Grub2 to control booting
3) /dev/sdc - Used for backups only (formatted as FAT32 so it's R/W in both Linux and Windows)

So I want to basically clone my Ubuntu 10.04 install that's on /dev/sdc onto /dev/sdb and get rid of Slackware altogether.  I'm having a hard time figuring out how to do this.  Last night I used Clonezilla to clone the Ubuntu 10.04 partition on /dev/sdc to /dev/sdb, but I think it ran into issues with the MBR.  I think Clonezilla only copies the MBR when you do a disk-to-disk clone, not a partition-to-disk.  So my question is what's the easiest way to do this?  Should I just clone the extended partition for Ubuntu 10.04 on /dev/sdc to /dev/sdb using ddrescue?  I also read where I can just boot a LiveCD for Ubuntu and almost just copy and paste the partition using GParted.  Any advice or direction is welcomed...

The reason for this is I want the bigger drive for backups and the /dev/sdb drive is much faster than the /dev/sdc.

---

### Post by bodhi.zazen on 2010-07-26
After you clone the partition you will need to:

1. Update grub.

Use a live CD and re-install

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Cloning the MBR will not help, as you moved the partition.

2. Update fstab. Again with a live CD, mount the ubuntu partition you moved at say /mnt and then open /mnt/etc/fstab and update it (swap/root/other partitions).

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by vttay03 on 2010-07-26
So is the easiest way to go about cloning it before those two things to just use something like gddrescue with the following:

```


ddrescue /dev/sdc1 /dev/sdb1


```

Where /dev/sdc1 is my extended partition for Ubuntu and /dev/sdb1 is the extended partition that I setup beforehand on the new drive.  I understand the fstab thing because I may need to change the UUID of the new drive since that is cloned as well.

---

### Post by vttay03 on 2010-07-27
Ok so I got everything cloned successfully, changed the UUID of the new drive and updated fstab to reflect this change.  I then was able to boot the LiveCD and reinstall Grub2 onto the new drive.  It was successfully installed because when I select that hard drive from a one-time boot menu, Grub comes up and gives me the options like I'm used to seeing.  However, when I select Ubuntu, it still boots the older drive.  Is there some type of conflict because I now have Grub2 installed to the MBR of two separate SATA drives installed into the same system?  I looked at the grub.cfg file of the new drive, and it still gives the UUIDs of the older drive, hence probably why it's booting that one.  Somehow I need to figure out how to run "update-grub" or something like that to point the new drive to itself instead of the older one.  Help please!!!!

---

### Post by linux18 on 2010-07-27
did you erase the old grub?

confirm this with someone else first, this command can be very dangerous:
```

sudo dd if=/dev/zero of=/dev/sdc bs=4096 count=1

```also, is you bios configured to boot from /dev/sdb?

---

### Post by vttay03 on 2010-07-27
Well, my plan (to be on the safe side) was not to erase the old disk until I got the new one up and running...which is why I have two disks installed into the system with Grub2 installed.  I think this should still work if I get everything configured correctly unless I'm overlooking something...

---

### Post by vttay03 on 2010-07-27
--I was able to get this all working by first manually editing the 'grub.cfg' on the new drive to reflect the new UUID.  This allowed me to boot the new drive so that I could run 'update-grub'.  Although this overwrote my manual edit of 'grub.cfg', it properly recognized the UUIDs of all the hard disks in my system so it didn't matter in the end.  

Initially I ran the following from old hard drive:

```

sudo grub-mkconfig -o /path/to/new/drive/grub.cfg

```

I thought this would be the ticket but for some reason it still generated a 'grub.cfg' with the wrong UUID of the new drive.  That's what ultimately led me to do what I described above.

---

