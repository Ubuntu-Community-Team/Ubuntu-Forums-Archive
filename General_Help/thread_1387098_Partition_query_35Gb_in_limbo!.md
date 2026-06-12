---
title: "Partition query: 35Gb in limbo!"
date: 2010-01-21
forum: General Help
---

### Post by hcs7dap on 2010-01-21
Dear community

I have recently setup my laptop to dual boot Win 7 and Karmic. Before I installed Karmic I shrank the space on one of the drives to accommodate Ubuntu.

However, when I put the live CD in the drive - it gave me the option of installing Karmic next to Windoze or in the free space that I had created. I chose it to go next to Win 7 because it inferred that a choice of OS would be given on boot up  by putting it next to Win 7.

However, I have a 35Gb 'unallocated' (as stated by GParted) - this is the space that I created but have not used. I wanted to remove this partition to maximise potential storage and would be grateful for advice on how this can be achieved.

Thanks in advance for your help

---

### Post by hcs7dap on 2010-01-23
bump

---

### Post by Elfy on 2010-01-23
boot the livecd - open partition editor from the sys admin menu.

Right click the swap partition and turn it off, you will be able to move the unallocated space and add it to existing partitions.

Or you could make a partition for data use, if you want to use it for both OS then make it ntfs

---

### Post by hcs7dap on 2010-01-23
I did as instructed... however, when I turned the linux swap off  - I still was unable to do anything with the unallocated space.

When I right click on the unallocated space the only options are: New and Information.

If I click on New - it says that I am unable to create more that 4 primary partitions. Information just gives the first/last/total sectors information.

Anyone?

---

### Post by plucky on 2010-01-23
Post a screenshot of your gparted window.

If your swap partition is in an extended partition,you have to increase the size of the extended partition first.

---

### Post by HermanAB on 2010-01-23
Note that in my humble experience, resizing partitions will sooner or later cause you to lose all your data...

So, I would leave the partitioning alone and just format the unallocated partition and mount it as /data or something.

---

### Post by hcs7dap on 2010-01-23
/home/hcs7dap/Desktop/Screenshot.png

Not really sure if this will work (screenshot) - I have cut and pasted it from the desktop and just got the line above.

Sorry... am new at this!

---

### Post by Jackzor on 2010-01-23
> **hcs7dap said:**
> /home/hcs7dap/Desktop/Screenshot.png

Not really sure if this will work (screenshot) - I have cut and pasted it from the desktop and just got the line above.

Sorry... am new at this!

Click the paperclip..

---

### Post by theozzlives on 2010-01-23
Windows 7 creates 2 partitions (system, drive C), you got your Ubuntu partition, and Extended (where Swap resides). That's 4 primary partitions. Move your Ubuntu partition so the free space is between Windows and Ubuntu, then use Disk Management in Windows to grow your Windows partition.

---

### Post by hcs7dap on 2010-01-23
Here is the screenshot. Do I need to boot from LiveCD in order to move the ubuntu partition?

---

### Post by Elfy on 2010-01-23
Yes you must boot from the livecd so that / is not mounted.

You will need to do a lot of partition moving though depending on where you want to add the space - the unallocated space has to be (as far as I know) to the right of the partition you wish to add it too.

So to add it to sda5 you would have to first move it past sda3 then past sda4 - then you can add it to the extended partition sda4 and then you can extend sda5 and increase it's size.

When you boot the livecd - you will have to make sure to swapoff - right click sdda6 and then swapoff

---

