---
title: "External hard drive keeps unmounting"
date: 2011-12-05
forum: General Help
---

### Post by layers on 2011-12-05
I have this hard drive which is from an old laptop, and i want to transfer all the files it had to my new one. I bought a kit with its power adapter and sata to usb cables, great. I hook it up, and I browse the two partitions it has. But when I try to copy something bigger than a .doc file, or sometimes when going through folders, the entire hard drive unmounts (not just that partition, but both). I cannot copy anything like this. Why is it happening and how can I stop it to unmount everytime it sees me?

---

### Post by oldtimer7777 on 2011-12-05
> **layers said:**
> I have this hard drive which is from an old laptop, and i want to transfer all the files it had to my new one. I bought a kit with its power adapter and sata to usb cables, great. I hook it up, and I browse the two partitions it has. But when I try to copy something bigger than a .doc file, or sometimes when going through folders, the entire hard drive unmounts (not just that partition, but both). I cannot copy anything like this. Why is it happening and how can I stop it to unmount everytime it sees me?

Did you try installing:
sudo apt-get install ntfs-3g

---

### Post by layers on 2011-12-05
> **oldtimer7777 said:**
> Did you try installing:
sudo apt-get install ntfs-3g

yes it is already its newest  version

I tried to take a snapshot quickly, because now, it just mounts and umnounts quickly without me doing anything. The second partition is shown as free, which is definately not true! THere are files in there and I can view them through file manager!

Update: and now i can even open it in file explorer. it unmounts that quickly!

---

### Post by layers on 2011-12-06
Now, it mounts, opens the folder, and then unmounts before I can even see anything! It's crazy! Is that a hardware issue?

---

### Post by Jay Car on 2011-12-06
> **layers said:**
> Now, it mounts, opens the folder, and then unmounts before I can even see anything! It's crazy! Is that a hardware issue?

A simple thing to try first might be to swap the USB cable (which might be faulty) for another one (if you have a spare). It's worth a try.  :)

Another thought...

You also might try a different USB port. I'm sure someone here will correct me if I'm mistaken, but external drives seem to have fewer problems when plugged in to the powered USB ports, usually the front ports on computers aren't powered, but the back ones are.  Or, you may have a USB hub that has powered ports.  Mine has two powered and the rest aren't. I don't know if it will help your problem, but it might be worth trying.

---

### Post by layers on 2012-03-01
A No Go.
I haven't been able to solve this problem. I have tried the usb on a different computer, with XP on it, exactly same thing. Could it just be a busted HDD? But I can still see the files on it for a few seconds... has anyone ran into such BS?

---

### Post by miasmablk on 2012-03-01
have you tried running a chkdsk or fsck on the drive for errors? perhaps it has bad sectors or maybe its mount point is corrupted.

---

### Post by layers on 2012-03-02
Well, as I expected, /media is empty. How would I chkdsk?

If I stalk it, for when it mounts for 2 seconds, I run fdisk -l, and it displays all local partitions instantly, then it hangs, waits before the external drive is unmounted, and then it returns to command line ready.

---

### Post by matt_symes on 2012-03-02
Hi

Unplug your external hard drive.

Open a terminal and type

```
tail -f /var/log/syslog
```

Plug in your external hard drive (there should be text about sensing the drive) and copy a file to it. 

When it remounts read only (or if it fails), stop tail with ctrl + c.

Post back the results of the tail. That may give clues as to what is happening.

Kind regards

---

### Post by layers on 2012-03-02
I really, need this fixed, thanks for all the help. A little background: This drive, if my memory is not lying, had ext3 and a NTFS Partiotins. There was Ubuntu installed on the ext3, and the old laptop (RIP) was booting from it. One day, I turned the machine on, the light turned on, black booting screen, and then everything went dead. So, ever since I remove the HDD and try to recover my files, this happens. Could the sudden power off during bootup have done something to it? Sometimes, if it stays mounted for more than 10 sec, I can see, and even copy little files from it.

matt_symes, I unplugged, ran the command, there were 7-8 lines originally displayed, I plugged the drive into the USB, after 3sec 4-5 more lines popped up, I saw the partitions in Nautalus, then after 1sec they unmounted and 8-9 more lines showed up, then I waited about 5sec and interrupted.

> ibo@ibo-VPCF130FD:~$ tail -f /var/log/syslog
Mar  2 20:29:30 ibo-VPCF130FD kernel: [ 9446.206780] sd 116:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Mar  2 20:29:30 ibo-VPCF130FD kernel: [ 9446.206783] sd 116:0:0:0: [sdb] CDB: Read(10): 28 00 04 51 c2 de 00 00 f0 00
Mar  2 20:29:30 ibo-VPCF130FD kernel: [ 9446.206789] end_request: I/O error, dev sdb, sector 72467166
Mar  2 20:29:30 ibo-VPCF130FD kernel: [ 9446.206805] JBD: Failed to read block at offset 6961
Mar  2 20:29:30 ibo-VPCF130FD kernel: [ 9446.206813] JBD: recovery failed
Mar  2 20:29:30 ibo-VPCF130FD kernel: [ 9446.206816] EXT3-fs (sdb3): error loading journal
Mar  2 20:29:30 ibo-VPCF130FD kernel: [ 9446.206820] sd 116:0:0:0: [sdb] Unhandled error code
Mar  2 20:29:30 ibo-VPCF130FD kernel: [ 9446.206822] sd 116:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Mar  2 20:29:30 ibo-VPCF130FD kernel: [ 9446.206824] sd 116:0:0:0: [sdb] CDB: Read(10): 28 00 04 51 c3 ce 00 00 10 00
Mar  2 20:29:30 ibo-VPCF130FD kernel: [ 9446.206830] end_request: I/O error, dev sdb, sector 72467406
Mar  2 20:30:08 ibo-VPCF130FD kernel: [ 9484.103822] usb 3-3: new high speed USB device using xhci_hcd and address 114
Mar  2 20:30:08 ibo-VPCF130FD kernel: [ 9484.126529] xhci_hcd 0000:05:00.0: WARN: short transfer on control ep
Mar  2 20:30:08 ibo-VPCF130FD kernel: [ 9484.127153] xhci_hcd 0000:05:00.0: WARN: short transfer on control ep
Mar  2 20:30:08 ibo-VPCF130FD kernel: [ 9484.127714] xhci_hcd 0000:05:00.0: WARN: short transfer on control ep
Mar  2 20:30:08 ibo-VPCF130FD kernel: [ 9484.128381] xhci_hcd 0000:05:00.0: WARN: short transfer on control ep
Mar  2 20:30:08 ibo-VPCF130FD kernel: [ 9484.129854] xhci_hcd 0000:05:00.0: WARN: short transfer on control ep
Mar  2 20:30:08 ibo-VPCF130FD kernel: [ 9484.130477] xhci_hcd 0000:05:00.0: WARN: short transfer on control ep
Mar  2 20:30:08 ibo-VPCF130FD kernel: [ 9484.131078] scsi117 : usb-storage 3-3:1.0
Mar  2 20:30:09 ibo-VPCF130FD kernel: [ 9485.124584] scsi 117:0:0:0: Direct-Access     WDC WD16 00BEVS-00RST0         PQ: 0 ANSI: 2 CCS
Mar  2 20:30:09 ibo-VPCF130FD kernel: [ 9485.125528] sd 117:0:0:0: Attached scsi generic sg2 type 0
Mar  2 20:30:09 ibo-VPCF130FD kernel: [ 9485.126679] sd 117:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Mar  2 20:30:09 ibo-VPCF130FD kernel: [ 9485.127059] xhci_hcd 0000:05:00.0: WARN: Stalled endpoint
Mar  2 20:30:09 ibo-VPCF130FD kernel: [ 9485.127901] sd 117:0:0:0: [sdb] Write Protect is off
Mar  2 20:30:09 ibo-VPCF130FD kernel: [ 9485.127909] sd 117:0:0:0: [sdb] Mode Sense: 28 00 00 00
Mar  2 20:30:09 ibo-VPCF130FD kernel: [ 9485.127915] sd 117:0:0:0: [sdb] Assuming drive cache: write through
Mar  2 20:30:09 ibo-VPCF130FD kernel: [ 9485.129815] xhci_hcd 0000:05:00.0: WARN: Stalled endpoint
Mar  2 20:30:09 ibo-VPCF130FD kernel: [ 9485.130430] sd 117:0:0:0: [sdb] Assuming drive cache: write through
Mar  2 20:30:10 ibo-VPCF130FD kernel: [ 9485.478228]  sdb: sdb1 sdb2 sdb3
Mar  2 20:30:10 ibo-VPCF130FD kernel: [ 9485.479264] xhci_hcd 0000:05:00.0: WARN: Stalled endpoint
Mar  2 20:30:10 ibo-VPCF130FD kernel: [ 9485.479928] sd 117:0:0:0: [sdb] Assuming drive cache: write through
Mar  2 20:30:10 ibo-VPCF130FD kernel: [ 9485.479937] sd 117:0:0:0: [sdb] Attached SCSI disk
Mar  2 20:30:10 ibo-VPCF130FD kernel: [ 9486.282137] EXT3-fs: barriers not enabled
Mar  2 20:30:11 ibo-VPCF130FD kernel: [ 9486.548920] xhci_hcd 0000:05:00.0: WARN: transfer error on endpoint
Mar  2 20:30:11 ibo-VPCF130FD kernel: [ 9486.662935] usb 3-3: reset high speed USB device using xhci_hcd and address 114
Mar  2 20:30:11 ibo-VPCF130FD kernel: [ 9486.684644] xhci_hcd 0000:05:00.0: WARN: short transfer on control ep
Mar  2 20:30:11 ibo-VPCF130FD kernel: [ 9486.684998] xhci_hcd 0000:05:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800ae05f880
Mar  2 20:30:11 ibo-VPCF130FD kernel: [ 9486.685001] xhci_hcd 0000:05:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800ae05f8c0
Mar  2 20:30:16 ibo-VPCF130FD kernel: [ 9492.440069] xhci_hcd 0000:05:00.0: WARN: transfer error on endpoint
Mar  2 20:30:17 ibo-VPCF130FD kernel: [ 9492.499701] usb 3-3: USB disconnect, address 114
Mar  2 20:30:17 ibo-VPCF130FD kernel: [ 9492.499757] sd 117:0:0:0: [sdb] Unhandled error code
Mar  2 20:30:17 ibo-VPCF130FD kernel: [ 9492.499762] sd 117:0:0:0: [sdb]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Mar  2 20:30:17 ibo-VPCF130FD kernel: [ 9492.499768] sd 117:0:0:0: [sdb] CDB: Read(10): 28 00 04 51 c2 de 00 00 f0 00
Mar  2 20:30:17 ibo-VPCF130FD kernel: [ 9492.499781] end_request: I/O error, dev sdb, sector 72467166
Mar  2 20:30:17 ibo-VPCF130FD kernel: [ 9492.499808] JBD: Failed to read block at offset 6961
Mar  2 20:30:17 ibo-VPCF130FD kernel: [ 9492.499821] JBD: recovery failed
Mar  2 20:30:17 ibo-VPCF130FD kernel: [ 9492.499827] EXT3-fs (sdb3): error loading journal
Mar  2 20:30:17 ibo-VPCF130FD kernel: [ 9492.499843] sd 117:0:0:0: [sdb] Unhandled error code
Mar  2 20:30:17 ibo-VPCF130FD kernel: [ 9492.499847] FAT: unable to read boot sector
Mar  2 20:30:17 ibo-VPCF130FD kernel: [ 9492.499852] sd 117:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Mar  2 20:30:17 ibo-VPCF130FD kernel: [ 9492.499859] sd 117:0:0:0: [sdb] CDB: Read(10): 28 00 04 51 c3 ce 00 00 10 00
Mar  2 20:30:17 ibo-VPCF130FD kernel: [ 9492.499876] end_request: I/O error, dev sdb, sector 72467406
^C
ibo@ibo-VPCF130FD:~$ 


---

### Post by matt_symes on 2012-03-02
Hi

> end_request: I/O error, dev sdb, sector 72467166
Mar  2 20:29:30 ibo-VPCF130FD kernel: [ 9446.206805] JBD: Failed to read block at offset 6961
Mar  2 20:29:30 ibo-VPCF130FD kernel: [ 9446.206813] JBD: recovery failed
Mar  2 20:29:30 ibo-VPCF130FD kernel: [ 9446.206816] EXT3-fs (sdb3): error loading journal

It looks to me like it's having trouble reading the journal. That may be due to a hardware issue or a corrupted filing system. I have seen both cause this error.

First thing i would do is run a SMART test on the drive. If the drive has SMART capability and SMART is enabled it will check the hard drive itself for problems. If the drive does not have SMART capability it will tell you. If it is disabled then post back and i will tell you how to enable it.

Open a terminal and type

```
sudo apt-get install smartmontools
```

Enter your password. It will not be echoed to the screen.

```
sudo smartctl -t long /dev/sdb
```

In the command above sdb is where your drives device node was created before. If it's created a different device node then change as appropriate.

It will take a while to run. It should tell you when it expects to finish. Give it ten minutes after that time and then type

```
sudo smartctl -a /dev/sdb
```

Check to see if has finished at check the status. If it says PASSED then, although the drive may has some damage, the drive thinks its still usable.

Post back the entire log of it anyway.

If it passes run a filing system check on the drive. The filing system is extX so you want to run fsck.

```
sudo fsck -f /dev/sdb1
```

This will force a filing system check. You may want to check the filing system before running the full check. You can do this with

```
sudo fsck -N /dev/sdb1
```

That will just tell you what it thinks is wrong with the filing system and not actually attempt to fix anything.

Post back on the outcome.

Kind regards

---

### Post by layers on 2012-03-02
good plan, but Disk Utility says Smart is not supported. I just checked again, you can see the pic in post #3. From where should I follow your commands again?

And I do not know where this is ("In the command above sdb is where your drives device node was created before."). When I run "fdisk l", it doesnt display the external partitions. I can see two directories in /media, but they unmount before I do anything. Should I just use sdb3?

---

### Post by efflandt on 2012-03-03
SMART does not work with USB connected drives (even wdc's own diagnostics).

It sure sounds like a hardware issue with the drive.

Some time ago I was trying to recover files from an old laptop (boss' grandsons) with just WinXP on it (which recognized a problem and refused to boot to preserve data).  From Ubuntu booted on CD I could not copy much from it before copying choked.  In an external enclosure it would not mount in Windows or Ubuntu.

I let it sit and about a week later connected the USB enclosure to Ubuntu desktop, it automounted and I copied most of the user's files from it, other than a game related directory with corrupted file(s).  So I just got lucky.

---

### Post by matt_symes on 2012-03-03
Hi

> **efflandt said:**
> SMART does not work with USB connected drives (even wdc's own diagnostics).

Sorry efflandt but this is not actually true.

This is for my external usb hard drive.

```
Mar  3 09:50:09 matthew-Aspire-7540 kernel: [53474.580302] usb 2-2: new high-speed USB device number 4 using ehci_hcd
Mar  3 09:50:09 matthew-Aspire-7540 kernel: [53474.720050] scsi3 : usb-storage 2-2:1.0
Mar  3 09:50:09 matthew-Aspire-7540 mtp-probe: checking bus 2, device 4: "/sys/devices/pci0000:00/0000:00:13.2/usb2/2-2"
Mar  3 09:50:09 matthew-Aspire-7540 mtp-probe: bus: 2, device: 4 was not an MTP device
Mar  3 09:50:10 matthew-Aspire-7540 kernel: [53475.725366] scsi 3:0:0:0: Direct-Access     Hitachi  HTS543216L9A300  0200 PQ: 0 ANSI: 4
Mar  3 09:50:10 matthew-Aspire-7540 kernel: [53475.729726] sd 3:0:0:0: Attached scsi generic sg2 type 0
Mar  3 09:50:10 matthew-Aspire-7540 kernel: [53475.733448] sd 3:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Mar  3 09:50:10 matthew-Aspire-7540 kernel: [53475.739854] sd 3:0:0:0: [sdb] Write Protect is off
Mar  3 09:50:10 matthew-Aspire-7540 kernel: [53475.739867] sd 3:0:0:0: [sdb] Mode Sense: 38 00 00 00
Mar  3 09:50:10 matthew-Aspire-7540 kernel: [53475.746340] sd 3:0:0:0: [sdb] No Caching mode page present
Mar  3 09:50:10 matthew-Aspire-7540 kernel: [53475.746353] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Mar  3 09:50:10 matthew-Aspire-7540 kernel: [53475.763808] sd 3:0:0:0: [sdb] No Caching mode page present
Mar  3 09:50:10 matthew-Aspire-7540 kernel: [53475.763826] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Mar  3 09:50:10 matthew-Aspire-7540 kernel: [53475.794402]  sdb: sdb1
Mar  3 09:50:11 matthew-Aspire-7540 kernel: [53475.816514] sd 3:0:0:0: [sdb] No Caching mode page present
Mar  3 09:50:11 matthew-Aspire-7540 kernel: [53475.816527] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Mar  3 09:50:11 matthew-Aspire-7540 kernel: [53475.816536] sd 3:0:0:0: [sdb] Attached SCSI disk
Mar  3 09:50:11 matthew-Aspire-7540 ata_id[4707]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
Mar  3 09:50:11 matthew-Aspire-7540 ntfs-3g[4722]: Version 2011.10.9AR.1 external FUSE 28
Mar  3 09:50:11 matthew-Aspire-7540 ntfs-3g[4722]: Mounted /dev/sdb1 (Read-Write, label "", NTFS 3.1)
Mar  3 09:50:11 matthew-Aspire-7540 ntfs-3g[4722]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177
Mar  3 09:50:11 matthew-Aspire-7540 ntfs-3g[4722]: Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096,default_permissions
Mar  3 09:50:11 matthew-Aspire-7540 ntfs-3g[4722]: Global ownership and permissions enforced, configuration type 7
```

```
matthew@matthew-Aspire-7540:~$ lsusb -d 1bcf:0c31
Bus 002 Device 004: ID 1bcf:0c31 Sunplus Innovation Technology Inc. SPIF30x Serial-ATA bridge
matthew@matthew-Aspire-7540:~$ 
```

```
matthew@matthew-Aspire-7540:~$ sudo smartctl -i /dev/sdb
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-15-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Travelstar 5K320
Device Model:     Hitachi HTS543216L9A300
Serial Number:    080903FB2200LCD20ZAA
LU WWN Device Id: 5 000cca 568cf03eb
Firmware Version: FB2OC40C
User Capacity:    160,041,885,696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3f
Local Time is:    Sat Mar  3 09:53:57 2012 GMT
SMART support is: Available - device has SMART capability.
**SMART support is: Enabled**

matthew@matthew-Aspire-7540:~$ 
```

And from there i can run a smart test.

I think it may depend on the circuitry of the hard drive enclosure as well as on the drive itself though.

You can look at the smart info of the drive with.

```
sudo smartctl -i /dev/sdX
```

where sdX is the device node.

> 
It sure sounds like a hardware issue with the drive.


I suspect you're correct here.

Kind regards

---

### Post by layers on 2012-03-03
> **efflandt said:**
> SMART does not work with USB connected drives (even wdc's own diagnostics).

It sure sounds like a hardware issue with the drive.

Some time ago I was trying to recover files from an old laptop (boss' grandsons) with just WinXP on it (which recognized a problem and refused to boot to preserve data).  From Ubuntu booted on CD I could not copy much from it before copying choked.  In an external enclosure it would not mount in Windows or Ubuntu.

I let it sit and about a week later connected the USB enclosure to Ubuntu desktop, it automounted and I copied most of the user's files from it, other than a game related directory with corrupted file(s).  So I just got lucky.

Yeah, exact same thing. Is there an alternative to SMART? Can I do anything to get the files from it?

---

### Post by matt_symes on 2012-03-03
Hi

Previously to SMART some drive makers produced DST (Drive self test) software.

Did you try fsck on the ext partition ?

Kind regards

---

### Post by layers on 2012-03-03
> **matt_symes said:**
> Hi

Previously to SMART some drive makers produced DST (Drive self test) software.

Did you try fsck on the ext partition ?

Kind regards

I don't know how.how would you so it?

---

### Post by Khayyam on 2012-03-04
> **matt_symes said:**
> [...]It looks to me like it's having trouble reading the journal. That may be due to a hardware issue or a corrupted filing system. I have seen both cause this error.

Matt ... look at '9446.206789' ... there is an I/O error prior to JBD trying to read the Journal. So, hardware.

layers ... how important is the data? If its v. important then boot off a rescue disk (like [SystemRescueCd]("http://www.sysresccd.org/SystemRescueCd_Homepage") or [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/")) and make a [ddrescue]("http://www.gnu.org/software/ddrescue/ddrescue.html") image of the disk and/or partition. You can then atempt to repair the image and not the disk. This is more work but has two main advantages 1. your image is not likely to fail in the process of repair and 2. you'll be working on a copy of the disk and not the disk itself.

A rescue CD wil not automount (gahhh) a failing drive (+5000 for that) .. which is why your seeing what your seeing.

By the looks of things the drive is failing ... matt's advice is solid, but for data that you really can't afford to loose additional measures should be taken .. ie: not working on a 'live' (and failing) disk.

A ddrescue image can be treated in the same way that you'd treat a partition, so fsck, and then try and mount it and copy off your data.

HTH ... khay

---

### Post by matt_symes on 2012-03-04
Hi

> Matt ... look at '9446.206789' ... there is an I/O error prior to JBD trying to read the Journal. So, hardware.

*Nods head in agreement*

ddrescue is an excellent idea and is something i do before i even look at someones computer if i suspect a drive problem.

You can play around with the image file till your hearts content.

EDIT:

Just a though and i suspect it's not your problem. 

Is the drive powered off the USB port ? If it is, are you sure there is enough power getting to it ? I have had this happen to me in the last couple of days when plugged into an external USB hub. It also had problems reading.

Kind regards

---

### Post by Khayyam on 2012-03-04
> **matt_symes said:**
> ddrescue is an excellent idea and is something i do before i even look at someones computer if i suspect a drive problem.You can play around with the image file till your hearts content.

Matt ... (helllo old chap!) ... ddrescue will also not balk at bad reads, I'll do it its best to copy the disk as is (bad sectors and all) which means that the copy will likely succeed. Other utilities will tend to want to make sure the copy is without error and so fail, which ends up just more strain on a (possibly) failing drive.

> **matt_symes said:**
> Just a though and i suspect it's not your problem. Is the drive powered off the USB port ? If it is, are you sure there is enough power getting to it? I have had this happen to me in the last couple of days when plugged into an external USB hub. It also had problems reading.

That might also cause I/O errors (as its throughput/hardware). The 'tail -f' doesn't show what spec the BUS is but the disk interface is USB3. The provison of power to devices is [one of the changes USB3 impliments](http://www.electronicscomponentsworld.com/articleView~idArticle~71587_1231512221012012.html) but obviously this would only be something a USB3 BUS would be capable of. Anyhow, USB3 is supposed to be "backward compatable", and so we can assume a USB3 device will have the same power requirements on a USB2 BUS as a USB2 device. So, this could indeed be an/the issue. My own USB3 2.5 case has small power socket (but no power addaptor was provided) so the issue may have been forseen WRT USB2 "backward compatability". If layers has a 2to1 USB cable s/he could try and use 2x USB slots to connect the drive and see if this causes the drive to power up correctly.

HTH and best ... khay

---

### Post by layers on 2012-03-06
Alright, I booted up from a 11.10 rescue CD, and it said I don't have some required sensor, so it put me in terminal screen. Luckily, ddrescue is already installed. I was on my way to mount all the partioions that I was going to use, I mounted the one I was going to save the .imbut I cannot mount the one I want to make the image of. Can someone help me mount it?
PS. It mounts sdb2 no problem thought. What's with sdb3 then?

---

### Post by Khayyam on 2012-03-06
> **layers said:**
> Alright, I booted up from a 11.10 rescue CD, and it said I don't have some required sensor, so it put me in terminal screen. Luckily, ddrescue is already installed. I was on my way to mount all the partioions that I was going to use, I mounted the one I was going to save the .imbut I cannot mount the one I want to make the image of. Can someone help me mount it?

ddrescue is like 'dd' you don't need to mount the disk to make an image, infact in your case its inadvisable.

best ... khay

---

### Post by layers on 2012-03-07
Alright, and it will save an image of the entire partition in an already existing folder?  There shouldn't be a problem if I am saving the image on a partition that I already have have some files on it right?

---

### Post by Khayyam on 2012-03-07
> **layers said:**
> Alright, and it will save an image of the entire partition in an already existing folder?  There shouldn't be a problem if I am saving the image on a partition that I already have have some files on it right?

Correct, the "image" is much like an ".iso" (CD image). The only issue you need to be aware of it the size of the image and the amount of available disk space.

best ... khay

---

### Post by layers on 2012-03-26
ok, so I finally got time to get this done, but there are more unexpected errors. Also, eventough the free space in the partition I want to place the image is more than 200GB, the image won't touch the rest of the files that are stored in the same partition, right?

---

### Post by rmil on 2012-03-26
Yes it just new file in your folder. Hence if you want to copy image of /dev/sdb3 try using simple method

```
sudo dd if=/dev/sdb3 of=/media/2/r/filename.iso
```

---

### Post by layers on 2012-03-26
nope, it just disconnects again. WIll it ever work?

---

### Post by layers on 2012-03-28
Should I just call the local computer store, or are they going to try the same thing I tried?

---

### Post by layers on 2012-04-02
I tried googling, but couldn't even find why it outputs:
```
ubuntu@ubuntu:~$ sudo ddrescue -r -3 -C /dev/sdb3 /media/2/r/image /media/2/r/logfile
ddrescue: Numerical argument out of limits.
```Does anybody know?

---

### Post by matt_symes on 2012-04-02
Hi

Are you sure enough power is getting to the drive ? 

I have seen this problem when an external drive is powered off the USB power supply. t did notice in  your first post that you said you had power leads for it. Are they supplying enough power ?

Also, are you using an external hub ? This has also caused me problems in the past.

I still think it may be hardware.

Kind regards

---

### Post by matt_symes on 2012-04-02
Hi

Are you sure enough power is getting to the drive ? 

I have seen this problem when an external drive is powered off the USB power supply. I did notice in your first post that you said you had power leads for it. Are they supplying enough power ?

Also, are you using an external hub ? This has also caused me problems in the past.

I still think it may be hardware.

As for ddrescue, i normally use something like this.

```
sudo ddrescue /dev/sdb3 /media/2/r/image
```

Have you considered taking the USB drive out the housing and trying it directly plugged in. Research your drive first to make sure you can do it with your model.

Kind regards

---

### Post by layers on 2012-04-02
> **matt_symes said:**
> Hi

Are you sure enough power is getting to the drive ? 

I have seen this problem when an external drive is powered off the USB power supply. t did notice in  your first post that you said you had power leads for it. Are they supplying enough power ?

Also, are you using an external hub ? This has also caused me problems in the past.

I still think it may be hardware.

Kind regards
The hard drive is an internal SATA. I have a kit, which I plug into the outlet, and then into the HDD. Then, a SATA cable transforms into a USB. Sorry I didn't address this misunderstanding earlier.[IMG]http://i01.i.aliimg.com/photo/v0/368541815/USB_To_SATA_IDE_2_5_3.jpg[/IMG]
and I'm using one of these USB ports on the side of my VAIO. It is blue.[IMG]http://www.laptopsindubai.com/wp-content/uploads/2010/12/sony_vaio1.jpg[/IMG]


I am using the exact hardware as in these pictures. (+WD Scorpio)
I did recall that I did try to just put it in a computer (inside). Same thing - unmounts.

No idea how to check if it gets enough power - the adaptor light shines green, it is connected to the USB port.
And, sure, if it is hardware, there is no way I can get the data back?

---

### Post by matt_symes on 2012-04-02
Hi

> I did recall that I did try to just put it in a computer (inside). Same thing - unmounts.

I would say you have exhausted every possibility by doing this step. I am 99% sure it's hardware (I am never 100% sure unless the hardware is in my hands). It also happens in XP so it's not software.

> And, sure, if it is hardware, there is no way I can get the data back?

Professional data recovery service ?

You can wait to see if anybody else has any ideas but i think the drive is a goner.

Kind regards

---

### Post by layers on 2012-04-02
Ok, I tried your command, and noticed something: it always unmounted at the same number of bytes rescued, and exactly when the error came up.

So, I tried to do "cp -r" to the whole drive, it unmounted. Then I tried to do it to individual folders deeper down, and it seemed that they copied ok. It really doesn't make sense to me, but I guess I'll try copying folder by folder.

---

### Post by matt_symes on 2012-04-02
Hi

> Then I tried to do it to individual folders deeper down, and it seemed that they copied ok.

That's a surprise. Maybe you can rescue data from the undamaged parts of the drive. (I stil think it's damaged but i may be wrong)

Get of as much as you can and the maybe run badblocks on the device after that.

Kind regards

---

### Post by layers on 2012-04-02
> **matt_symes said:**
> Hi



That's a surprise. Maybe you can rescue data from the undamaged parts of the drive. (I stil think it's damaged but i may be wrong)

Get of as much as you can and the maybe run badblocks on the device after that.

Kind regards

So, what is happening then? I'll try to find a pattern of this unmounting (I'm hoping it would unmount only when I touch specific bytes, which would mean that most of the data is infact ok)

---

### Post by matt_symes on 2012-04-02
Hi

> **layers said:**
> So, what is happening then? I'll try to find a pattern of this unmounting (I'm hoping it would unmount only when I touch specific bytes, which would mean that most of the data is infact ok)

It may be bad blocks (unreadable sectors) on the drive the that are causing the problem.

The output from syslog a number of posts back suggested that was a problem as it could not read them.

This suggests physical hard drive damage but i have not seen it unmount a drive before and ddrescue has always managed to at least skip bad blocks (fill with zeros) when i have used it (the drive you are rescuing should *not* be mounted when using ddrescue; only the partition you are copying to).

Get as much data off as you can and try running badblocks.

EDIT: It's very late here and i am off to bed now. Good luck.

Kind regards

---

### Post by layers on 2012-04-02
> **matt_symes said:**
> Hi



It may be bad blocks (unreadable sectors) on the drive the that are causing the problem.

The output from syslog a number of posts back suggested that was a problem as it could not read them.

This suggests physical hard drive damage but i have not seen it unmount a drive before and ddrescue has always managed to at least skip bad blocks (fill with zeros) when i have used it (the drive you are rescuing should *not* be mounted when using ddrescue; only the partition you are copying to).

Get as much data off as you can and try running badblocks.

EDIT: It's very late here and i am off to bed now. Good luck.

Kind regards

thanks for all the help. go to bed.

---

### Post by ALUKARDH3LLS1NG on 2012-04-02
hey guys total noob here, probably my first post but I'm having a strange issue. I scoured the forums and google but just not to sure as to how state the question to get a response. My issue is related to external/internal drives so i thought id post here so here goes, I put an empty sd card into my desktop then proceeded to reboot and start from a windows xp cd (yeah i know but the wifey insists on windows) and installed xp onto the sd card thinking i can boot from it on my labtop and wife will be happy. well that didnt work out it didnt boot and to top it off it erased grub from my desktop. No problem boot from live cd and repair that, all went well but now my second internal hdd is not mounting, its being detected but not mounting also anything i plug in is not mounting nothing at all. I run lsusb in terminal and it shows me my drives they just wont mount. Im running ubuntu 11.10 64bit any help is greatly appreciated and again thank you, sorry for being a noob or maybe posting in the wrong section.

---

### Post by layers on 2012-04-02
> **ALUKARDH3LLS1NG said:**
> hey guys total noob here, probably my first post but I'm having a strange issue. I scoured the forums and google but just not to sure as to how state the question to get a response. My issue is related to external/internal drives so i thought id post here so here goes, I put an empty sd card into my desktop then proceeded to reboot and start from a windows xp cd (yeah i know but the wifey insists on windows) and installed xp onto the sd card thinking i can boot from it on my labtop and wife will be happy. well that didnt work out it didnt boot and to top it off it erased grub from my desktop. No problem boot from live cd and repair that, all went well but now my second internal hdd is not mounting, its being detected but not mounting also anything i plug in is not mounting nothing at all. I run lsusb in terminal and it shows me my drives they just wont mount. Im running ubuntu 11.10 64bit any help is greatly appreciated and again thank you, sorry for being a noob or maybe posting in the wrong section.
haha "probably" your first post - you nailed that one right. :D

umm, you should probably try to make a new thread, and explain just the problem (and type in a more paragraphed manner, a big blob like this is hard to read).

From what I can understand, drives are not mounting. 

[http://ss64.com/bash/mount.html](http://ss64.com/bash/mount.html)

Have you tried mounting it manually? The "mount -a [] []" command? If that works, then you don't have auto mounting on.

---

### Post by layers on 2012-04-02
> **matt_symes said:**
> Hi



It may be bad blocks (unreadable sectors) on the drive the that are causing the problem.

The output from syslog a number of posts back suggested that was a problem as it could not read them.

This suggests physical hard drive damage but i have not seen it unmount a drive before and ddrescue has always managed to at least skip bad blocks (fill with zeros) when i have used it (the drive you are rescuing should *not* be mounted when using ddrescue; only the partition you are copying to).

Get as much data off as you can and try running badblocks.

EDIT: It's very late here and i am off to bed now. Good luck.

Kind regards

ooh, one last question: let's say I do manage to recover all the data files from root - how can I resurrect the system? Just putting the files on top of a working installation definitely won't work.

---

### Post by ALUKARDH3LLS1NG on 2012-04-03
> **layers said:**
> haha "probably" your first post - you nailed that one right. :D

umm, you should probably try to make a new thread, and explain just the problem (and type in a more paragraphed manner, a big blob like this is hard to read).

From what I can understand, drives are not mounting. 

[http://ss64.com/bash/mount.html](http://ss64.com/bash/mount.html)

Have you tried mounting it manually? The "mount -a [] []" command? If that works, then you don't have auto mounting on.
 Yes I've tried this to no availability, I mean I'm stumped I've done all sorts of google searches but can't get nowhere. Hey but thanks allot for your reply. I'll start a thread soon but navigating this forum seems difficult it's nothing like xda or rootzwiki where I practically live:D

---

