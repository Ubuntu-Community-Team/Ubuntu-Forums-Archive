---
title: "Trying to Uninstall and Delete Partition"
date: 2010-10-09
forum: General Help
---

### Post by bryce1 on 2010-10-09
Hello all,

Sorry if this is more than a general help question. A few months ago I decided to install ubuntu as a separate partition on my laptop which already had Windows 7. I am finally ready to remove it because I need the extra hard drive space.

**So:** I have downloaded G-Parted and boot from the disk. When i select all the default settings, I am getting a "fatal server error no screens". 

Here are my specs: (I believe my video card is a Mobile Intel GMA 4500 HD)


OS Name	Microsoft Windows 7 Home Premium
Version	6.1.7600 Build 7600
Other OS Description 	Not Available
OS Manufacturer	Microsoft Corporation
System Name	BRYCEMONTANO-PC
System Manufacturer	Hewlett-Packard
System Model	HP Pavilion dv6 Notebook PC
System Type	x64-based PC
Processor	Intel(R) Core(TM)2 Duo CPU     P7550  @ 2.26GHz, 2266 Mhz, 2 Core(s), 2 Logical Processor(s)
BIOS Version/Date	Hewlett-Packard F.36, 10/9/2009
SMBIOS Version	2.4
Windows Directory	C:\Windows
System Directory	C:\Windows\system32
Boot Device	\Device\HarddiskVolume1
Locale	United States
Hardware Abstraction Layer	Version = "6.1.7600.16385"
User Name	BryceMontano-PC\Bryce Montano
Time Zone	Mountain Daylight Time
Installed Physical Memory (RAM)	4.00 GB
Total Physical Memory	3.91 GB
Available Physical Memory	2.37 GB
Total Virtual Memory	7.81 GB
Available Virtual Memory	6.06 GB
Page File Space	3.91 GB
Page File	C:\pagefile.sys


Anyone have any ideas what to do? Ideally I want to remove the unbuntu partition and give Windows 7 all the HD space.

Thanks for your time,

Bryce

---

### Post by Mark Phelps on 2010-10-09
The first thing you should do BEFORE you mess with any partitions is to use the Win7 Backup feature to create and burn a Win7 Repair CD.  You will need that later to repair the MBR.

Then, use the Win7 Disk Management tool to remove the partition and either (1) expand the Win7 OS partition to fill the space or (2) create a new NTFS partition in its place.

Then, boot from the Win7 Repair CD, enter command mode, and enter "bootrec.exe /fixmbr"

That should restore your original MBR and allow you to boot directly into Win7 again.

If that doesn't work, reboot from your Win7 Repair CD and run  Startup Repair three times -- that's three times, not once or twice.

Also, in future, if you have Win7 questions, you should go to the premier Win7 forum to get answers -- sevenforums.com.

---

### Post by bryce1 on 2010-10-16
Thanks so much for the response, sorry for my late response at that.

I have a few questions before I try this. I remember I tried a similar technique a while back and when I deleted the volume first that went fine and then once the volume was deleted I then tried to delete the partition and it would not allow me to.

Does that sound familiar at all?

Second, you said:

"Then, boot from the Win7 Repair CD, enter command mode, and enter "bootrec.exe /fixmbr""

So when I boot from the Win7 repair CD there will be an option to run command mode?



**EDIT:** As I thought, when I deleted the volume, it left with me with a "free volume" partition and when I try and delete the partition it says:

"There is not enough space on the disk(s) to complete this operation"

Any suggestions?

Thanks again,

Bryce



**EDIT #2** I was able to figure out the command part. Worked perfect, but i'm still unable to delete the free space partition. It still says : "There is not enough space on the disk(s) to complete this operation". 

I also tried to extend my C: partition but that area is grayed out. Any other suggestions?

---

