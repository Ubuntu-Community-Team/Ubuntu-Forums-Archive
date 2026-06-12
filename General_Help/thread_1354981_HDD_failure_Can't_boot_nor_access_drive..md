---
title: "HDD failure? Can't boot nor access drive."
date: 2009-12-14
forum: General Help
---

### Post by vest1 on 2009-12-14
Hi

I'm trying to access a dual-boot Ubuntu/XP HDD. Booting into Windows returns an instant error, filesystem unknown. Booting into kubuntu gives me a error that goes something like this, repeats a few times, same thing in rescue mode.

exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
cmd c8/00:f8:bc:90:17/00:00:00:00:00/e4 tag 0 dma 126976 in res 40:00:00:00:00/00:00:00:00:00/00 Emask 0x4(timeout)

After that it tells me it can´t mount and that no init is found, then it goes into BusyBox.

I´m booting the computer up from the newest Ubuntu 9.10 cd and I get the following error messages when I try to read the two main partitions I'm interest in:

NTFS partition:

Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x00000088 size: 1024
usa_ofs: 0 usa_count: 65535: Invalid argument
Record 6 has no FILE magic (0x88)
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount 'dev/sda2': Input/output error
NTFS is either inconsisten, or there is a hardware fault, or it's a SoftRaid/FakeRAID hardware. In the first cas run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details.

The linux Ext3 partition gives the error

UNable to mount location
DBus error org.freedesktop.DBus.Error.NoReply: Did not recieve a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Anyone got any advice on how I can get to the files on the drive? It's a 80gb drive that's split between the two OS's.

Thanks,
vest1

---

### Post by cariboo on 2009-12-14
Did you try your Windows install CD to boot in to a recovery console and the suggestion of chkdsk /f to try and repair your Windows partition? you can run fsck from the live CD to see if that will repair your Ubuntu partition. I would also suggest you download the diagnostic tools from your hard drives manufacturers web site and run them to see if it is a problem with the hard drive.

---

