---
title: "Finding Ubuntu partition"
date: 2011-06-19
forum: General Help
---

### Post by ScroobeX on 2011-06-19
Hello,

I have a problem with Ubuntu which resulted in 11.04 basically being unusable, therefore I need to reinstall or format the ubuntu partition.

However, I created two partitions on the disk, C (windows) and D (Linux) but the D has become invisible, cannot be seen.

Would someone know how to make it "reappear" so I can reinstall Ubuntu on it? 

Thanks!

---

### Post by JRV on 2011-06-19
Are you trying to look for a Linux partition from Windows?
Windows will not see it.

Can I see a copy of your partition table?

Boot from the live CD, select try Ubuntu, open a terminal and enter:
```
sudo parted -l
```

And post the result.

(That is a lower case "L".)

---

### Post by ScroobeX on 2011-06-20
Thanks for your reply.

I have done what you said from very Ubuntu (got no CD ROM) and here's what I got:

```
Model: ATA TOSHIBA MK1655GS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition table: msdos

No    Beginning  End    Size        Type    File system     Indicators
 1    32,3kB   80,0GB  80,0GB    primary   ntfs             boot
 2    80,0GB   160GB   80,0GB    extended
 5    80,0GB   160GB   80,0GB    logical   ext4

```What I really had in mind is if the partition can be "brought back" i.e. formatted and then use wubi to install Ubuntu properly on D partition, since it's just a netbook, no CD drive.

---

### Post by JRV on 2011-06-21
Wubi is an option to try Ubuntu, it is not good for a permanent installation, updates are often a problem. (My opinion)

I would delete the logical drive (/dev/sda5) and the extended partition (/dev/sda2) and do a full install to the unused space.  The guided installation should set-up the dual boot and create a swap file as well as the main ext4 partition for Ubuntu.

You would have to re-format the partition in NTFS to install Wubi.

There are people more qualified to give you advice than I when it comes to Wubi.  Start by checking out the Wubi Megathread here:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by ScroobeX on 2011-06-21
Yes, that is exactly what I want to do, deleting or formatting those partitions in order to do a fresh install, but I don't know how to do that from ubuntu.

When I mentioned wubi I said that because I do not have a cd rom on the netbook so it's more convenient.

---

### Post by -kg- on 2011-06-21
You can burn the Live CD to a USB flash drive and boot/install from that.  You can use the Windows-based [Unetbootin]("http://unetbootin.sourceforge.net/") to create the bootable Flash drive.  You can then install or do whatever partitioning you want to from that.

---

### Post by ScroobeX on 2011-06-21
Thanks -kg- for telling me about unetbootin, never tried it, but I might give it a shot.

Txs both of you guys.

---

### Post by JRV on 2011-06-21
Yes, unetbootin is the way to go.

---

### Post by ScroobeX on 2011-06-21
Yeah it sure is, have installed unetbootin and installed ubuntu, it worked like a charm!!!

Txs again, you have made my day.

Greetings from Ubuntu!

---

