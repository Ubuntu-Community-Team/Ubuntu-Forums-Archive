---
title: "how to file bug report"
date: 2011-06-05
forum: General Help
---

### Post by the wolfe on 2011-06-05
How do I go about filing a bug report with the installer for ubuntu 10.04 and 11.04? The ubuntu website only has methods to report a bug once installed. Im having issues with the installer. 
1. its duplicable with multiple downloads and CD burns along with the USB installer. 
2. Only on the HM55 chipset (mobile i3/i5/i7) platform
3. cross brands (Acer, HP, Dell, and Asus). 
4. Tried and unable to duplicate with different chipsets and platforms (SB, Athlon II, Phenom II, C2D, C2Q, Desktop i3,i7)

so, how do I go about reporting this problem to Ubuntu, so that hopefully there will be a fix soon.

---

### Post by wgarcia on 2011-06-05
You have to decide on which package is affected (ubiquity?) and enter in a terminal 

ubuntu-bug ubiquity

Then in the ensuing form you enter all details that you can and step-by-step report on how to reproduce it.

---

### Post by the wolfe on 2011-06-05
I dont have a clue what package is affected. 
The issue is on laptops with the HM55 chipset, the installer will recognize the NTFS partition on there, and shows the right name, but doesnt recognize it as a OS, thus does not have a install beside option. 

Which package would cover that?

---

### Post by Quackers on 2011-06-05
There could be reasons for that other than the installer (ubiquity) having a bug.
Please give details of your current partition layout and partition types (eg primary/logical). 
Is there any free space for Ubuntu to install into?
These are just a couple of possible reasons for what you are experiencing.

---

### Post by the wolfe on 2011-06-05
the layout is 14.3GB restore partition NTFS, 582GB Windows 7 (NTFS) install with 67GB used. It has plenty of room to install. 

Plus if it was a partition issue, that dont explain why it dont work across the whole platform as I have been able to test it.

---

### Post by Quackers on 2011-06-05
Is your only "free space" within the 582GB NTFS partition, or is there other free space outside of any partition?

---

### Post by the wolfe on 2011-06-05
I assume that there is more floating somewhere. Its a 640GB HDD, and its only showing 596GB available. Thats 44GB missing somewhere.

---

### Post by Quackers on 2011-06-05
The amount of space used by formatting a 640GB disc can easily amount to 44GB being lost.
If you have no free space outside of a formatted partition there is nowhere for Ubuntu to install to.
If you have a look in Windows Disk Management console you can see whether any space is shown as unallocated.
You can also look there to see how many primary partitions are currently being used by Windows and any recovery partition etc etc.

---

### Post by the wolfe on 2011-06-05
[IMG]http://i1096.photobucket.com/albums/g322/wolfeking/Untitled-8.jpg[/IMG]
thats what the partition manager is showing currently.

---

### Post by Quackers on 2011-06-05
Your hard drive is full at the moment - even though there is free space within partitions, it is not usable space.
In order to create space for another operating system you should first defragment your C: drive in Windows. Twice would be better.
Then in the Disk Management console you can right-click on the C: drive and select "shrink". In the new window you can then choose how much to shrink the C: partition by. 
After shrinking (which only takes a few seconds) you will see some "unallocated space" appear in that window.
That space can then be used by Ubuntu.

---

### Post by the wolfe on 2011-06-05
ok. ill try this and see if it fixes it.

---

### Post by the wolfe on 2011-06-05
that worked. thanks man. 

But 1 question. Why didnt I have to do that on my other tries with older systems and AMD powered versions of the one I have?

---

### Post by Quackers on 2011-06-05
You're welcome :-)  Glad it worked.
Maybe on the other systems there was free space. It's not really possible to say for sure without seeing the details.
Happy Ubuntuing :-)

---

### Post by the wolfe on 2011-06-05
it should be easy going now. 
11.04 still uses the same codes to enable the DVD as 10.04 did, correct.

---

