---
title: "recover partition with bad sectors"
date: 2009-06-29
forum: General Help
---

### Post by vladk2k on 2009-06-29
Hello everybody

I have an Ubuntu (8.04.2) Server whose primary hard disk drive went rapant and developed bad sectors, to the point where it would not boot.

I have used Hiren's boot cd to run a surface test and identified the bad sectors (around 1050, most of them below LBA 1,000,000, all of them below LBA 2,000,000), after which I ran the "attempt repair - medium speed" which seems to have worked flawlessly.

The hard disk drive was partitioned into sda1 (10 GiB, /), sda2 (65 GiB, in a software raid 1 with sdb1 as /home) and sda3 (512 MiB, swap). I also have two other hard disk drives, sdb (which has 10 GiB of "volatile" data) and sdc (which is completely formatted as NTFS). All data partitions are ext3.

Now I'm in a bit of a pickle, with two problems to solve (I';; go in-depth with each one):
[LIST=1]
[*]How to recover some of the data on sda1 (samba config file, dhcp config file etc.)
[*]What hard drive to install the new operating system on
[*]What will happen with file permisions?
[/LIST]

Problem number one is this: I've yet to boot into a liveCD to be able to work with advanced tools (mainly because of the crap CD-ROM I have - should be fixed soon). However, I started a debian netinstall and its partitioner was able to see both partitions on sda, so I'm kind of hoping there is some readable content there.
Is there a way to mount a damaged file system (even as read-only) and read data from it? what about reconstructing the folder tree?

Problem number two: sda1 is the first 10 GiB of sda. sdb2 is the last 10 GiB of sdb (I've stated earlier that sda2 and sdb1 are software raid 1). If I install again into sda1, is it prone to developing more bad sectors? Would installing into sdb2 be a problem, since it's largely at the back of the partition?
I will of course swap the disks on the IDE cable so that sda becomes sdb and viceversa, but will it al be for nought?

Problem number three: the software raid was mounted under /home, so that I don't have problems with /home/samba (which consists of the most critical files). However, the new users might not get the same uid (and what about gid?) so will accessing the files be a problem, or will it be as simple as [FONT="Courier New"]chown -R[/FONT] as root?

Please respond, I'd like to get the server back online ASAP.

---

### Post by vladk2k on 2009-06-30
Ok, so seeing how nobody answered, I made a backup (read *dd if=/dev/sda1 of=/mnt/backup* ) of the partition and overwrote it with the new filesystem

What would you recommend to get text files (smb.conf, dhcpd.conf etc.) out of it? I played a little with *less* but it's pretty tenuous.

---

### Post by automaton26 on 2009-06-30
If a disk develops more then a couple of bad sectors I usually bin it - in my experience it is far more likely to develop more and more bad sectors over time.

I seem to remember that **foremost** is good for retrieving images, and may allow some configuration for other file types.

I've heard of something called testdisk, but never investigated further. There must be some good software out there to recover files, because it's a common requirement, and manually using a sector editor and hex editor would take ages.

Anyone ?

---

