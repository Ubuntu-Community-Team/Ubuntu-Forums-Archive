---
title: "multiple USB/ESata drives batch partition/multiply"
date: 2012-09-15
forum: General Help
---

### Post by hagrid on 2012-09-15
Dear Ubuntu Application Developers,

I am not a Linux expert but I consider Ubuntu a great distribution.
That's why I choose it to use as my primary workstation OS. I think that an OS should be an environment for our work and not the object of our work. And my work on this OS is primary to clone USB HDD Drives and USB Memory sticks. So, to be more specific, I have to write, lets say 150GB of data on 15 USB HDD which must be ext3 formatted or write approx. 3,5GB data on 20 USB Memory sticks which must be formatted before as ext2.
I must create a good workflow for this jobs but I cannot find any application able to batch format and copy to these drives. My computer has 2 esata ports and 8 USB3 ports where I can connect by now 4 7port USB 3.0 hubs. So the hardware is in place but a good software is missing. 
For now I use GParted for partitioning and format but when you need to format 20 USB drives that are mounted you have to unmount each(which takes approx 30 second each for 4GB USB Memory sticks) and then delete and create partition. Well, this looks ok with some limitations but when it comes to copying... you have to make it manually... And after 9 paste's I have to wait to finish to continue with the other drives...
That's why I come to experts to help me find the fastest way and proper tools to complete my workflow.
Thank you.

---

### Post by cariboo on 2012-09-16
@hagrid, this sub-forum is for those that need help creating programs for Ubuntu. I'll move this thread to a sub-forum, where the real experts, our members, can answer your question. Moved to General Help.

---

### Post by dcstar on 2012-09-16
> **hagrid said:**
> Dear Ubuntu Application Developers,

I am not a Linux expert but I consider Ubuntu a great distribution.
That's why I choose it to use as my primary workstation OS. I think that an OS should be an environment for our work and not the object of our work. And my work on this OS is primary to clone USB HDD Drives and USB Memory sticks. So, to be more specific, I have to write, lets say 150GB of data on 15 USB HDD which must be ext3 formatted or write approx. 3,5GB data on 20 USB Memory sticks which must be formatted before as ext2.
I must create a good workflow for this jobs but I cannot find any application able to batch format and copy to these drives. My computer has 2 esata ports and 8 USB3 ports where I can connect by now 4 7port USB 3.0 hubs. So the hardware is in place but a good software is missing. 
For now I use GParted for partitioning and format but when you need to format 20 USB drives that are mounted you have to unmount each(which takes approx 30 second each for 4GB USB Memory sticks) and then delete and create partition. Well, this looks ok with some limitations but when it comes to copying... you have to make it manually... And after 9 paste's I have to wait to finish to continue with the other drives...
That's why I come to experts to help me find the fastest way and proper tools to complete my workflow.
Thank you.

All the tools are there already.

You use "parted" to partition and format the devices, then you can use "dd" to copy an entire existing partition or many of the various file copy tools to copy data. Then you unmount the devices with the "umount" command.

**You** should look at the man pages for all of these tools to learn how to use them to achieve what **you** want to do.

---

