---
title: "Boot Problems with 12.04"
date: 2012-04-29
forum: General Help
---

### Post by usmcfieldmp on 2012-04-29
Having problems booting into 12.04. First off, I'm fairly lacking on proper terminology and I know next to nothing about advanced Linux troubleshooting.

On a cold start/restart, the computer will go through it's normal process, but seems to sit for a while at the Ubuntu load screen. After a little bit, it'll move to a terminal like screen in the upper left corner that reads:

> BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)[Flashing Underscore]

I can't seem to do anything from that screen though. Enter, Esc, "help"... nothing seems to work other than a restart.

When I restart it, it'll go to the launch screen giving me the options of:

> Ubuntu, with Linux blah blah blah
Ubuntu, with Linux blah blah blah (RECOVERY MODE)
Previous Linux versions
Memory Test (?something?)
Memory Test (?something?, serial console ?numbers?)

I selected the regular boot once, and it basically gave me a similar screen as before, only this time it had this just above it:

> /dev/disk/by-uuid/1dc5de84-9b4d-46d8-af1f-2005d56da982 does not exist



By selecting Recovery Mode, it'd give me the recovery options screen. I've ran dpkg (repair broken packages) and fsck (check all file systems)... seemingly to no avail. When I selecting resume (resume normal boot)... it takes me to the log-in screen just fine. No log-in problems, either.



I searched through here looking for an answer, but saw nothing. Saw some recommendations to run 'Boot-Repair' for other Boot problems, so I do. Results: [http://paste.ubuntu.com/954171](http://paste.ubuntu.com/954171)

Made some videos of what it's doing... but they pretty much just show exactly what I described above. Here's one showing the initial start-up, problem, restart, etc. It says it won't be live for another 20min (Midnight - Central Time)

[http://youtu.be/TV2Z5M60k2k](http://youtu.be/TV2Z5M60k2k)

---

### Post by oboedad55 on 2012-04-29
What kind of computer is this, Mac, PC, laptop? Need more info. I did find this: [http://ubuntuforums.org/showthread.php?t=1898901](http://ubuntuforums.org/showthread.php?t=1898901)

---

### Post by usmcfieldmp on 2012-04-29
Video that follows the second: [http://youtu.be/tMgPmoUpRa0](http://youtu.be/tMgPmoUpRa0)

Just shows me hitting resume from the recovery screen and it starting fine.

> **oboedad55 said:**
> What kind of computer is this, Mac, PC, laptop? Need more info. I did find this: [http://ubuntuforums.org/showthread.php?t=1898901](http://ubuntuforums.org/showthread.php?t=1898901)

I do appear to be missing the /dev/disk/by-vid/ folder and it's contents - which is what the earlier error pertained to. I don't know that the missing folder/files is all of my problem, but I have confirmed that it isn't there.



Gen3 Dell XPS

[LIST]
[*]Pentium 4 Processor 550 (3.4GHz) w/ HT Technology and 1MB cache
[*]1GB DDR2 SDRAM at 533MHz (Soon to be 3GB)
[*]256MB PCI Express x16 (DVI/VGA/TV-out) ATI Radeon X800 XT
[*]250GB ATA Maxtor 7V250F0 (Just benchmarked - Min: 21.8Mb/s Max: 55.9Mb/s Avg: 42.8Mb/s Average Access Time: 15ms)
[*]Sound Blaster Audigy 2 THX
[/LIST]

---

### Post by usmcfieldmp on 2012-04-30
CORRECTION... I had previously typed in that the address was "/dev/disk/by-vid"... but after seeing it again, it's "by-uuid". I checked the file, and it IS in the folder... so I'm not sure what the error is for. Start-ups are becoming harder and harder. I used to be able to simply select recovery mode and it would take me straight to the log-in screen. That's not the case anymore. I tried a regular start-up and a start-up in recovery mode about 5 times each with no success. Finally just started it up using "a previous version of Linux" and it took me through the Ubuntu load screen and then to the Log-in screen.

Here are some pics that I took with my phone.

[IMG]http://i138.photobucket.com/albums/q268/USMCFieldMP/Mobile%20Uploads/IMAG0135.jpg[/IMG]

[IMG]http://i138.photobucket.com/albums/q268/USMCFieldMP/Mobile%20Uploads/IMAG0136.jpg[/IMG]

[IMG]http://i138.photobucket.com/albums/q268/USMCFieldMP/Mobile%20Uploads/IMAG0137.jpg[/IMG]

---

### Post by usmcfieldmp on 2012-04-30
Reading around, trying to figure somethings out. Ran some tests that were recommended:

> _____@_____:~$ sudo blkid
[sudo] password for _____: 
/dev/sda1: UUID="1dc5de84-9b4d-46d8-af1f-2005d56da982" TYPE="ext4" 
/dev/sda5: UUID="7f189944-27ae-4ea5-aa01-e5b35ccdd448" TYPE="swap" 


_____@_____:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00064e99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   482279423   241138688   83  Linux
/dev/sda2       482281470   488280063     2999297    5  Extended
/dev/sda5       482281472   488280063     2999296   82  Linux swap / Solaris
_____@_____:~$ 


---

