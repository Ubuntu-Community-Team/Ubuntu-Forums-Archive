---
title: "accessing Vista files through Ubuntu"
date: 2010-07-13
forum: General Help
---

### Post by DrJordo on 2010-07-13
Didn't know where to put this, so the mods can move it if needed.

Today I managed to corrupt Windows Vista. It froze during a defrag, I'm guessing that restarting caused it to corrupt. I am currently running Ubuntu on a USB stick. I don't think i'll be able to repair Vista (I don't have the disk because Vista was pre-installed), so I need to know how I can move my data elsewhere before I install Ubuntu permanently.

---

### Post by TheStroj on 2010-07-13
It's really simple. If you can run Ubuntu it's no problem. 

When you're on your Ubuntu desktop, go to Computer and go into windows partition (it will be listed there). Now you can simply copy files to another device.

---

### Post by DrJordo on 2010-07-13
Unfortunately, doing that gives me this error:

Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x31380001  size: 4096  usa_ofs: 14134  usa_count: 24869: Invalid argument
Actual VCN (0x7475656e3d656761) of index buffer is different from expected VCN (0x5).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

does this mean that my data is lost?

---

### Post by Pogeymanz on 2010-07-13
Your data probably isn't lost yet.

Is your hard drive arranged in a RAID?

You might be able to find a downloadable Windows Checkdisk CD to run the mentioned command on that partition.

You might also look into "Super Grub Disk" which has some hard drive tools.

---

### Post by DrJordo on 2010-07-13
Found a CD, I'll post again when I have tried using chkdsk. Thanks for the help.

---

### Post by kdford on 2010-07-13
I was able to get around this by mounting the USB drive in a Windows XP VM (running under Ubuntu / VirtualBox), with USB Enabled (non open-source edition of VirtualBox).

When I was under windows, I could run chkdsk -F and that fixed the corrupted entries.  The file that was corrupted was zeroed out by the chkdsk process but it was completely munged anyway so I didn't really lose anything.

The original corruption, in my case, came from a laptop overheating during a large Virtual Appliance export to an external drive.  The laptop overheated at the 15GB mark and just powered off, causing the file to be corrupted.

---

### Post by mr clark25 on 2010-07-13
which version of ubuntu is on your usb drive?

if it is 10.04, i would check the smart status of the drive...

you can do this under system>administration>disk utility

EDIT: i posted this before your latest post, so it sounds like your hard drive is probably good.

---

### Post by Twitch6000 on 2010-07-13
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

The following link links to a vista recovery cd. after you burn it do disc run it. It will run a scan to fix your problem.

---

