---
title: "Bios disk read error.. Grub rescue"
date: 2011-06-24
forum: General Help
---

### Post by sss_sss on 2011-06-24
Hi,
Yesterday morning I switched on my laptop as usual and shockingly it did not go as usual :(( It was not at all booting up. I did not do any installations or partitions before that. My laptop has only single partition with Ubtuntu-9.10 installed. It is showing fallowing error:
 
**Grub loading**
**Bios disk read error**
**Grub rescue>**
 
After this nothing is happening. What could be the problem?
I have seen some posts in this forum and google but nothing is helpful for me. So please help me in this situation. I don't want to loose my data and I need to work on my laptop.
 
sss_sss

---

### Post by ohadcn on 2011-06-24
do you have the live cd?
try reinstalling grub
[https://help.ubuntu.com/community/Grub2#Reinstalling GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB2")

---

### Post by Rubi1200 on 2011-06-24
Before you consider reinstalling GRUB, post the output of the boot info script so we can get a better idea of what is where on the system:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by psusi on 2011-06-24
9.10 has reached end of life and is no longer supported; you need to upgrade.

As for your error, it looks like either your disk has become corrupted or is failing.  Boot from the livecd and open the disk utility and check the SMART status of the drive.

---

### Post by walter_j on 2011-06-24
do you have a usb stick attached? I can get a message like that when grub tries to boot a usb drive that doesn't have a os on it.

---

### Post by sss_sss on 2011-06-25
Hi Rubi,
Thanks for your quick reply. I have fallowed what you suggested. I have downloaded the script and ran it. Here are the results:

At terminal fallowing output is shown:

[B]"gawk" could not be found, using "/usr/lib/initramfs-tools/bin/busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
no block devices found

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Desktop/".
[/B]
Here is the RESULTS.txt file's content:

#################################################################
[B]                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================


============================ Drive/Partition Info: =============================

no valid partition table found
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/ramzswap0                                          swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (rw)
/dev/sr0         /cdrom                   iso9660    (rw)

[/B]
**========= Devices which don't seem to have a corresponding hard drive: =========**

**no block devices found **

#################################################################

So, what should I do know? Am I going to loose my data and hard drive :(
Please suggest me what to do next.

Thanks in advance.
sss_sss

---

### Post by Rubi1200 on 2011-06-25
Did you check the SMART status as psusi suggested?

What does it show?

---

### Post by sss_sss on 2011-06-26
Hi,
I tried to check the SMART status of the drive but when I open the disk utillity it is showing SMART is not available. I have no idea what to do next.
 
Regards,
sss_sss

---

### Post by Rubi1200 on 2011-06-26
Whatever you do, try not to write any data to the disk as I suspect it might be failing. 

Go to the website of the manufacturer and see if there are any utilities available for download that can be used to check disk integrity and see what they report about the health of the disk.

Are you able to see any of your data on the disk when using the LiveCD? If yes, copy and save as much as you can now.

---

### Post by sss_sss on 2011-06-27
Hi,
In my system, disk utility is showing only CD/DVD drive. It is not recognising/showing  hard disk information. I think I have lost my hard drive :( but is there any way to get my data?


Regards,
sss_sss

---

### Post by psusi on 2011-06-27
Not if the drive is gone, no.

---

### Post by Wim Sturkenboom on 2011-06-27
> **sss_sss said:**
> Hi,
In my system, disk utility is showing only CD/DVD drive. It is not recognising/showing  hard disk information. I think I have lost my hard drive :( but is there any way to get my data?


Regards,
sss_sss

Put the disk in another PC (as a second drive) and see if a tool like photorec can help; not sure if it can.

If not, it might be a very expensive exercise to get your data back.

---

