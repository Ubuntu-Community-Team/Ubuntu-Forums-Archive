---
title: "Trouble Booting &amp; Reading Data from SSD"
date: 2012-07-21
forum: General Help
---

### Post by Jack Of Clubs on 2012-07-21
Hey all,

I'm running into some problems with Kubuntu all of a sudden.  Yesterday the computer was running poorly, and after a restart it came up with:

```
error: hd0 out of disk
press any key to continue...
```

... and then dropped me into the BusyBox built-in shell, which I've never been in before.

I heard that the "out of disk" error can be a problem with grub, so I booted from an image and was going to see if that was the problem.  However, my attempt to mount the drive yields this:

```
kubuntu@kubuntu:~$ sudo mount /dev/sda1 /mnt
mount:	wrong fs type, bad option, bad superblock on /dev/sda1,
	missing codepage or helper program, or other error
	In some cases useful info is found in syslog - try
	dmesg | tail  or so
```

dmesg then yields:

```
kubuntu@kubuntu:~$ dmesg | tail
[  659.228555] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  659.228555] Descriptor sense data with sense descriptors (in hex):
[  659.228555] 		72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[  659.228555] 		02 c1 56 18
[  659.228555] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  659.228555] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 02 c1 56 18 00 00 10 00
[  659.228555] end_request: I/O error, dev sda, sector 46224920
[  659.228555] JBD2: recovery failed
[  659.228555] ata1: EH complete
[  659.228555] EXT4-fs (sda1): error loading journal
```

I'm at a loss.  I suspect an issue with the drive; it shows up in the BIOS at full size, but it won't mount from its slot or if connected via USB (RunCore SSDs have a Micro socket built in).  Anyone have any ideas?

In case you need the info, it's a Dell Mini 9 with a 32GB RunCore SSD and 2GB of memory.

---

### Post by kyphi on 2012-07-21
Assuming that you have your entire operating system on that drive with only one partition, you have installed too many programs.

If you continue to do so you will end up with a black screen and command line access only.

To check your disk usage, open a terminal and type ```
df -h
```
That will show you (as a percentage) how much is where.  Would you please post the result with your reply.

---

### Post by Jack Of Clubs on 2012-07-21
Hi kyphi,

Booting from USB, I can't even mount the drive to get df to show me how full it is, and I know I haven't come close to filling it yet.  From the BusyBox shell, this is all it gives me (it won't allow the -h parameter):

```
Filesystem	1024-blocks	Used Available Use% Mounted on
udev		  1014884	 184   1014700   0% /dev
```

---

### Post by kyphi on 2012-07-21
No matter about the "h" parameter (h stands for human readable).

The error message says that the disk is running out of space yet the latest figure you provided shows that the disk is hardly used.  However, since the file system seems to be corrupted and cannot be read I regretfully have to agree with your own diagnosis that the SSD is no longer usable.

---

### Post by Jack Of Clubs on 2012-07-21
Yeah, that's what I was afraid of.  Thankfully, the only critical thing on the SSD is some Dungeons & Dragons notes, although if I can find some utility that lets me recover them I'll be happy.

Thanks for your help! :)

---

### Post by kyphi on 2012-07-21
The information on this URL may be of help to you:

[http://www.linuxtoday.com/it_management/2010022800535OSSWRL](http://www.linuxtoday.com/it_management/2010022800535OSSWRL)

Good Luck.

---

### Post by Jack Of Clubs on 2012-07-21
Thanks again!  I found a utility that will let Win7 read ext4 volumes and was able to retrieve my home directory.  A subsequent format later, I can't reinstall on the SSD, so I'm pretty sure it's bad.

---

### Post by oldfred on 2012-07-22
Did you try e2fsck? That often repairs file systems like a chkdsk in Windows.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by emagar on 2012-07-23
I am relatively new to linux. I did something awfully wrong trying to  install an on-line thesaurus for emacs. Now the machine will not boot  all the times. Re-starting the machine will take me to BIOS boot  sequence, as if the hard drive (which is a SSD) were not bootable. 

This  behavior is not systematic. The  machine did in fact boot correctly after switching it off and on for a few  times.  I've been hesitant to reboot again, but my wife  inadvertently turned the machine off, and the same pattern occurred: two  failed boot attempts and a successful third. 

How can I figure out what is broken?

Thanks in advance for your advice, I am at a loss.

---

### Post by oldfred on 2012-07-23
First look in log files. Use Log File Viewer and open dmesg. I should show the current boot and several previous versions like dmesg.0 or .1 etc. If not shown in default you have to open it from /var/log.

Look for some driver or device that takes a very long time, or repeats & fails.

If you had abnormal shutdowns the e2fsck could still help. Every 40 or 60 boots it runs fsck and if any issues may run it. That can slow booting by several minutes.

---

### Post by emagar on 2012-07-24
> **oldfred said:**
> First look in log files. Use Log File Viewer and open dmesg. I should show the current boot and several previous versions like dmesg.0 or .1 etc. If not shown in default you have to open it from /var/log.

Look for some driver or device that takes a very long time, or repeats & fails.

If you had abnormal shutdowns the e2fsck could still help. Every 40 or 60 boots it runs fsck and if any issues may run it. That can slow booting by several minutes.

Thanks OldFred. I have looked at dmesg logs but cannot figure out much, long and cryptic.

I'll boot from usb and attempt e2fsck on unmounted drive. I'll report back when done.

---

### Post by Jack Of Clubs on 2012-07-25
> **oldfred said:**
> Did you try e2fsck? That often repairs file systems like a chkdsk in Windows.

Hey oldfred,

I tried e2fsck with both sets of parameters that you listed; it gives me an output like dmesg gave me above, and concludes with a warning that the filesystem still has errors.  I think it's busted.

Thankfully, the drive is under warranty and I have a spare I can use in the meantime just to get a working install going.

---

