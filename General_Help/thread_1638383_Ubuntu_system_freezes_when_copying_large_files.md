---
title: "Ubuntu system freezes when copying large files"
date: 2010-12-05
forum: General Help
---

### Post by happymellon on 2010-12-05
I am copying some files from a RAID 0 to a single disk, which are quite large at around 50 GB each.
Dragging and dropping in Nautilus, and using cp produce the same affect, whereby only a piece of the file is copied and the system becomes unresponsive to mouse/kb or ssh but I am still able to get a ping response. I've left it in this state for and hour but it never returned, and with no activity lights flashing I doubt it is still doing anything.

Looking through dmesg, debug, messages in the system log viewer doesn't show any entires at that time, it jumps from disk is mounted, a single entry for a pulse audio event suppressed and then to kmsg started.

Does anyone have any ideas on how to increase the level of logging for cp, to see if there is something locking up, or if there is another log to check?

Background: This is a new spare hdd that I was backing up files to before breaking down the RAID-0 to convert it to a RAID-5. Since it is new I have attempted to format it both EXT4 and then EXT3 in case it was a bug in EXT4, but it occurs in both formats. The RAID-0 was originally created on Ubuntu 9.04, until 10.10 came out and I finally ran the upgrade, so the files were originally created on a previous version.

Thanks,

H.

**UPDATE**
So it looks like it is soft locking on me, when the system reaches locking up point it no longer responds to my input but if I change to an alternative TTY before lockup I get print outs talking about soft lockups from kswap but only to me terminal, not to any log file. It seems to be happening in Red Hat too, who pushed out a patch on Saturday.

[https://bugzilla.redhat.com/show_bug.cgi?id=649694](https://bugzilla.redhat.com/show_bug.cgi?id=649694)

I've moved to launchpad as I've had no response here: 
[https://answers.launchpad.net/ubuntu/+source/linux/+question/136929](https://answers.launchpad.net/ubuntu/+source/linux/+question/136929)

**Last update**
Received this confirmation:
Peter Sorensen wrote 9 hours ago:	 #1
Running vmlinuz-2.6.35-23-generic on compaq v2000 (amd sempron proc) system freezes on copying large files.
running vmlinuz-2.6.35-22-generic there haven't been any problems. The current kernel freezes consistently on about 1gig of transfer. The only option is to power off.

If you having this issue, try and boot from a previous kernel.

---

