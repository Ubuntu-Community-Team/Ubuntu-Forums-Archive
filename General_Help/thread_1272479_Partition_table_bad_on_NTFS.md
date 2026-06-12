---
title: "Partition table bad on NTFS"
date: 2009-09-22
forum: General Help
---

### Post by ralphy on 2009-09-22
On the same disk, I have installed Win XP (on the primary partition, NTFS) and Ubuntu (on a logical partition).
I use Partition Magic as a boot loader.
I have a logical partition formatted as FAT, which contains a directory of eBooks I read from both XP and Ubuntu.

After cleaning out a virus, it seems my partition table is suddenly messed up.

In Ubuntu, I can connect ok to my eBook directory on the FAT partition without a problem.
In GParted, the partition table looks good, all correct and nothing missing.

However, in XP, in Explorer:
- In Explorer, while the C disk, in Explorer, seems to be working ok, if I select the FAT drive, XP asks me if I want to format it.
- in the Computer Management>Storage>Disk Management dialog, the Volume List panel is empty.


Any ideas as to why the partition table is a problem in XP but not in Ubuntu - don't they get their information from the same place on the MBR?
Any pointers on how to correct the partition table as seen from Windows?
Any help appreciated.

Alan

---

### Post by P4man on 2009-09-22
Thats funny :)
One would indeed expect XP and linux to read FAT partitions in a very similar way, but apparently not. The only thing I can think off is that ubuntu still has an fstab entry, and perhaps that allows it to know stuff about the partition that windows doesnt? Seems unlikely, but like I said, I got no clue either.

---

### Post by ralphy on 2009-09-22
The fstab entry works ok and GParted shows the partition data (start and end locations) correctly. If there's no easy fix, I suppose I could rely on the Gparted data as a basis for manually re-creating the partition table from the XP side (hmmm, am I about to hose my PC? How does one go about this?)

---

### Post by louieb on 2009-09-22
Take a look at the partition table. See if anything seems odd. post the output from:

```
sudo fdisk -l
``` lowercase L at the end

---

### Post by fishyf on 2009-09-22
That's an interesting one.

I suspect that the partition type is what is causing the problem for windows. See [http://ubuntuforums.org/archive/index.php/t-579677.html](http://ubuntuforums.org/archive/index.php/t-579677.html)

Here is one approach. If you happen to have a spare disk of the same or larger size which you can overwrite, then get windows to create the same partitions on that disk. You could then compare the two partition tables. The primary partition table is very short: 4 entries of 16 bytes each.

Assuming /dev/sda is the hard disk, you can try
sudo dd if=/dev/sda bs=1 skip=446 count=64 | xxd -g1

This will show you four lines which correspond to the four entries of the partition table. In each line, the 5th entry corresponds to the partition type. 83 is a Linux partition, you will probably see that in your case. Anyway, windows can complain if the partition type is incorrect.

You can play around with fdisk if you want. You might be worried about damaging your partition table. No panic, back it up first.

I suggest you boot from a boot CD or USB key, and backup your master boot record (which contains your partition table) onto a usb key. e.g. try 
sudo dd if=/dev/sda count=1 > /media/usbkey/partition.backup

Then fdisk to your heart's content. If it doesn't work ... and you want to go back to the old partition table then restore using 
sudo dd if=/media/usbkey/partition.backup of=/dev/sda

Warning: this doesn't apply to extended partitions!

More information at [http://www.priscilla.com/Courses/ComputerForensics/pdfslides/01-PC_Partitions.pdf](http://www.priscilla.com/Courses/ComputerForensics/pdfslides/01-PC_Partitions.pdf)

---

### Post by ralphy on 2009-09-23
Problem solved :-)
Thank to louieb for your interest, and your intructions, priscilla, I'll use them to backup my MBR.

In the User Guide for Partition Magic, under Troubleshooting, Partition Tables and Viruses found this clue:
'If partition changes made under one operating system are not reflected under another, and vice versa, a master boot record (MBR) virus may be present.'

Googling around this, I found the solution here:
[http://forums.cnet.com/5208-7588_102-0.html?threadID=337729&start=15&tag=forum-w;forums06](http://forums.cnet.com/5208-7588_102-0.html?threadID=337729&start=15&tag=forum-w;forums06)

In case this link breaks, what the article essentially says is that the problem is caused by a rootkit that hides malicious processes.
There is a free tool to fix this, McAfee Rootkit Detective Version, available here:
[http://vil.nai.com/vil/stinger/rkstinger.aspx](http://vil.nai.com/vil/stinger/rkstinger.aspx)

The Disk Administration now shows both the primary and the logical FAT partition, and if I select the FAT disk in Explorer, it no longer asks to be formatted and shows all my Ebooks once more. Phew.

---

