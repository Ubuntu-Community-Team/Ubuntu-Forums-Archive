---
title: "Installing Ubuntu Between XP"
date: 2009-07-18
forum: General Help
---

### Post by mrnt3250 on 2009-07-18
I need to install ubuntu between XP.
I have two drives (C and D) D drive have 11 GB free disk space and C drive have 14 GV free disk space.
I have some of emergency files and i didnt like to lose them!
first i try to install ubuntu from windows but after some days i get BusyBox Error (GRUB).
Now i need to install it dual with xp.
how i can install **Without Losing Data**.

thanks.

---

### Post by mikewhatever on 2009-07-18
The only way not to lose data is to have it safely backed up.

---

### Post by naklinaam on 2009-07-18
There are a couple of guides (which I am sorry, I am too lazy to google up right now).
But here are some basics you need to do:

1. defrag your c drive. This is very important in order to make some space for the ubuntu partiion(s).

2. [optional but highly highly recommended] Backup your critical emergency files onto D Drive if 11 GB is enough (it should eb for most really critical files) or better still back it up on external media - CD/DVD/ External Hard Disk or USB flash sticks etc.

3. Pop in your Ubuntu LiveCD and reboot your machine.

4. You will getan option to either install the OS directly or to go into Ubuntu for testing without installing. I usually use the later option. Dont know why, but it just feels "safer"

5. Now when you double-click the icon to install ubuntu and follow through the process, one of the options you will get is to choose between installing on the entire disk (and overwrite whatever you have on the disk) or to install side-by-side (called dual boot). MAke sure to chose this option.
The best option is to select the manual option for the partitions so you can knowingly resize your windows partition and install ubuntu in the space freed up by resizing the windows partition.

The installer will then guide you through the partition changes and show what it is doing graphically before committing it. 
Please note that changes to partitions can get a little messy and there is n element of risk involved but in the 5-7 times that I have installed and reinstalled ubuntu in the past few weeks, I have not lost any windows data in the process.
Just carefully read through each message and warning and make the appropriate choice rather than just clicking through with defaults.

Hope this gives you some direction and confidence to go ahead and do it.
especially if you have backed up your data.
Please also note that if you install ubuntu on C Drive for example, it will not even touch your D Drive and that data is safe unless you select a wrong option in the partition manager.

---

### Post by mrnt3250 on 2009-07-18
thanks to mikewhatever and naklinaam.
i have another question.
my files is very very important and i will pay to safe my files. (buy new hard drive).
i will use only new hdd and i will install ubuntu in new hard, after that if i need to active that drive and using XP - UBUNTU, what i have to do?

---

### Post by naklinaam on 2009-07-18
> **mrnt3250 said:**
> thanks to mikewhatever and naklinaam.
i have another question.
my files is very very important and i will pay to safe my files. (buy new hard drive).
i will use only new hdd and i will install ubuntu in new hard, after that if i need to active that drive and using XP - UBUNTU, what i have to do?

Once you get the new HDD, just hook it up to your computer when installing ubuntu and chose that drive for ubuntu. The system will automatically take care of allowing the current XP to remain as is and boot ubuntu only off the external drive. 

However, given the criticality of your data, I would recomend that you copy all this data to the external hard disk and use C Drive for ubuntu.
Why, you ask? Because if you have the data on an exernal disk and if you need to go anywhere (especially if you are rushing out is some emergency) you can carry this drive with you and all its data as well.

Now what would you rather be able to carry with you - this critical data or a free downloadable os?
Another thing I recommend (in case you choose to keep the data on the external drive) is to format his external drive in FAT32 or some format compatible with Windows so your data is truly portable and can be access from other machines as well if required.
Within the wondows formats, FAT16/FAT32 are most portable but cant handle individual files great than 4GB, while NTFS can. Although Windows and Linux can both read / write NTFS data, I am not sure about other operating systems.

---

