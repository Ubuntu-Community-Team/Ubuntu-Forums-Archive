---
title: "Ubuntu + Software Raid + Large Storage"
date: 2011-03-13
forum: General Help
---

### Post by mitchmalone on 2011-03-13
I am currently in the process of digitizing all of my media and putting my DVD's, CD's etc. into storage that will be network accessible. As a result I require an excessively large storage setup and I also want this to be quite safe and therefor constantly backed up.

I am confident with Linux and have used Ubuntu / Red Hat / Fedora for several years, but I have never worked much with large storage. In particular, I want multiple drives to behave as a single drive and I also want to RAID mirror the setup.

Ideally, this is the setup I am going for a setup like this.
- Running Ubunto 10.10
- 12TB of media storage, 5 x 2TB WD Drives - I've checked, my motherboard can do this.
- This equates to 6TB of actual storage once it is RAID mirrored.

What I am not too sure on is the following:
- What are the requirements to make multiple drives show up as a single accessible directory? i.e. I want to be able to see 6TB of storage as a single drive with all of the media on it and not have to worry about viewing the mirrored copies.
- What software is required to set up the RAID?
- Are there any tutorials for something like this?

Any help in these matters would be terrific, even if it's just links to tutorials as I am finding it hard to find the right tutorials.

---

### Post by xfacta on 2011-03-14
I use mdadm for mirror of 2 sata drives(RAID 1), I believe it will support almost any reasonable config you like, and the new "Disk Utility" in the Administration menu recognises everything as you'd expect.
After initial set up about 2 years ago, I can even do a clean install of the OS on the old IDE system disk then just install MDADM and it finds my sata drives and I'm back in action. (I use simple backup too, and I grab a copy of /etc before doing a clean install)

This updates the config:
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf

This shows detail if you don't like the new disk util gui:
sudo mdadm --detail /dev/md0

Keep in mind that if you use a disk util or OS (particularly Windows!) to join disks into one larger disk (RAID 0) you can possibly lose everything if you lose one disk. I think you mean you will be using something like RAID 5 in which case you would be pretty safe.

---

### Post by xfacta on 2011-03-14
Once you've got MDADM all set up and working, mount the new disks into the filesystem somewhere.
1st create a path for it, I used /store, then add an entry to fstab like:

/dev/md0	/store		ext3 defaults 0 0

adjust to suit your filesystem.

I am NOT booting off the multidisks, I am booting of a single replaceable IDE disk with OS and swap, all the good data is on RAID 1 disks.

All I did was read up on MDADM

---

### Post by xfacta on 2011-03-14
This will do for starters:

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

But just google mdadm for more

---

