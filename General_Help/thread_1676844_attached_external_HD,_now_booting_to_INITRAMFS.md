---
title: "attached external HD, now booting to INITRAMFS"
date: 2011-01-27
forum: General Help
---

### Post by mjhess on 2011-01-27
I am dealing with a bad harddrive that caused my Ubuntu install to no longer work.
I'm stuck with INITRAMFS.

The situation:
I'm running Ubuntu 10.04 off an external harddrive attached to an old Windows box. Grub is installed on the HD, so when the harddrive it not plugged in, Windows is none the wiser. That has been working great. I ran into trouble with an old 120 GB Harddrive that stopped in the middle of a file transfer on the Windows side, no grinding noise or other failure signs. But it hung. When I reconnected the harddrive in Windows it said "Drive must be formatted before it can be used."

I decided to start into Linux, to see if I could see anything on the drive. Plugging in the drive caused Ubuntu to freeze (ie if the focus was on a terminal, the terminal would hang until the drive was unplugged - or it would hang for minutes). So I restarted Ubuntu, with both the harddrive and the ubuntu drive to be plugged into USB ports. It booted into a black screen with the line "Cannot boot OS."

Fine, restart Linux, and now it starts into a lot of text and INITRAMFS. If I restart with recovery mode, I get the same thing.

What do I do now?

I don't understand what could have caused this, or what is actually happening. Did the system try to boot the bad harddrive first and did that cause changes to GRUB on the second harddrive and so now it cannot boot?

I don't have a live CD (this was installed off a USB drive), but will create one if necessary. I have a netbook that is running 10.10 (only), and could plug the ubuntu drive into it for troubleshooting, but would I risk corrupting another system?

Any suggestions?

Thank You,
Mike

---

### Post by mjhess on 2011-01-28
One followup:
I ran a Ubuntu 10.10 Live CD. The external harddrive having the main Ubuntu system I am trying to get access to, is seen as a 497GB Filesystem in Nautilus, but cannot be mounted:

Unable to mount 497 GB Filesystem
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

I looked at gparted and it shows the drive as sdd 
sdd1 ext 4 boot
sdd2 extended
sdd5 swap

If I look at dmesg | grep sdd I get
[INDENT][  126.471055] sd 7:0:0:0: [sdd] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[  126.471582] sd 7:0:0:0: [sdd] Write Protect is off
[  126.471585] sd 7:0:0:0: [sdd] Mode Sense: 23 00 00 00
[  126.471588] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[  126.473283] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[  126.473291]  sdd: sdd1 sdd2 < sdd5 >
[  126.510793] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[  126.510798] sd 7:0:0:0: [sdd] Attached SCSI disk
[  126.878216] EXT4-fs warning (device sdd1): ext4_clear_journal_err: Filesystem error recorded from previous mount: IO failure
[  126.878223] EXT4-fs warning (device sdd1): ext4_clear_journal_err: Marking fs in need of filesystem check.
[/INDENT]When I run filesystem check via
sudo fsck -f /dev/sdd1
I get
[INDENT]fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sdd1
Filesystem mounted or opened exclusively by another program?
[/INDENT]I don't quite understand how to fix the Filesystem error,
or what would be using that filesystem exclusively before it is mounted?

Is there some process I would have to manually stop before I can run the filesystem check?

Any suggestions as to what else to try?

Thank You,

[B]Mike
[/B]

---

### Post by mjhess on 2011-01-29
OK, I'm back in business.

There was some process running on the LiveCD that kept me from running fsck on the harddrive. Since the LiveCD is "fixed", I wasn't sure if you could set configuration switches and have those stick in a reboot. If you can't adjust this, the LiveCD was not an obvious fix.

I ended up installing Knoppix 6.2 onto a flash drive. Start into text only mode, insert the bad harddrive, check dmesg and it recognizes the harddrive just fine as /dev/sdg. Ran fsck on /dev/sdg1 and got:

recovering journal
clearing orphaned inode ...
(about 12 of those)

It came back saying
/dev/sdg1 clean

Quit Knoppix, restart PC with harddrive attached, and voila everything is back without any bad side effects. Phew.

Sorry this is a non-ubuntu solution on a ubuntu forum.
Did not know if this was still appropriate to post, 
but maybe this workaround will save a Ubuntu user in the future.

---

