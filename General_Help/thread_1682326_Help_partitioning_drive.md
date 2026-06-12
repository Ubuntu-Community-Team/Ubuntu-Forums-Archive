---
title: "Help partitioning drive"
date: 2011-02-05
forum: General Help
---

### Post by andywhoa on 2011-02-05
My machine is running Windows 7, but I've decided to dual-boot Ubuntu.

I'm on the manual partitioning screen.

Originally, the Windows drive took up the whole drive.  I took 100 GB off of it to use as an Ubuntu drive.  From that, I created the swap partition.  Afterwards, I decided I wanted some more space for Ubuntu; so I took another 40 GB off of my Windows partition.

Now I have 2 free space partitions.  How can I combine them?  It seems I'm only allowed to install Ubuntu on one or the other.

Thanks for your help.

---

### Post by andywhoa on 2011-02-05
Ah, I see. The swap partition was between the two free space partitions.  I removed the swap partition and the free space partitions combined.


:guitar:

---

### Post by glene77is on 2011-02-05
[SIZE=3]> **andywhoa said:**
> 
[SIZE=2]My machine is running Windows 7, but I've decided to dual-boot Ubuntu.
I'm on the manual partitioning screen.[/SIZE][/SIZE]> **andywhoa said:**
>  [SIZE=3][SIZE=2]
Originally, the Windows drive took up the whole drive.  I took 100 GB off of it to use as an Ubuntu drive.  From that, I created the swap partition.  Afterwards, I decided I wanted some more space for Ubuntu; so I took another 40 GB off of my Windows partition.
Now I have 2 free space partitions.  How can I combine them?  It seems I'm only allowed to install Ubuntu on one or the other.
Thanks for your help.[/SIZE][/SIZE][SIZE=3]

Andy,
My main computer has Win-XP and Ubuntu, dual booting. 
Linux Ubuntu only needs 3 G to load, so 10 G partition works very well. 
Linux only needs 2 G. 
Linux can use the remainder as data storage partitions, archives, etc. 

These are what my Ubuntu setup the last time I did an auto install. 
If you create a partition,  and install Ubuntu, 
then Ubuntu will write that disk address 
into the Master Boot Record (MBR).  
If you alter the location of the initial boot code, 
by "Resizing" the partition, 
then the MBR will point to a non-booting spot on the HD. 

I suggest that you use GpartEd for partition building.  
This is the GNU Partion Editor, 
and can even be obtained on a Live-CD 
to use for recovery of systems. 
The GUI and the presentation is well designed.  
GpartEd will not let you re-size some partitions for the above reason, regarding the location of the initial boot track-sector.  
Unfortunately, I have altered a partition anyway, 
and found out the hard way that the disk becomes unbootable. 

So,  
if I were installing Ubuntu, or Knoppix, or Puppy, etc, I would run  GpartEd  and create a large Extended partition right next to the Windows OS.   I would then create several smaller partitions inside the Extended partition, and create a Swap partition at the far end of the hard drive space.    The several partitions inside of the Extended partition could be combined, however I prefer having several 20 G partitions. 

I want to add something here.  
(1) I suggest you use the GpartEd application for Disk Partitioning. 
The operations are graphically presented, and are clear to see. 
(2) In my experience, if you install Linux OS into a partition that begins immediately after the Windows partition, then you can "Resize" it later; that is, you can "Resize" it on the right end by adding or subtracting disk space.    The left end (beginning) is where the initial boot track-sector is defined and this location is written into the Master-Boot-Record (MBR).   

This is the method I have used in my development computer, which boots into Ubuntu sda5 as primary, with the Grub options to boot into 
(1) Puppy 
(2) Knoppix 6.2
(3) Knoppix 6.4
(4) Ubuntu 10.4    
(5) WATT OS R2
The MBR points into Ubuntu sda5, runs grub.cfg, generates the menu. 
I used GpartEd to shuffle disk space, and observed the fixed location of the Ubuntu's initial boot track-sector, on sda5,  which was written into the MBR. 

If the Linux OS is installed in the third or fourth, etc. partition away from the Windows partition,    and then you try to combine ("Resize")  per GpartEd may  warn you that the HD may become un-bootable.  

The reason for that problem is that the MBR is pointing literally to a track-sector to initiate the boot sequence,  and you have just moved that code to somewhere else (and who knows exactly?).   During an install, Ubuntu will install an MBR which points to the current boot track-sector of the currently installing OS.   
  
I apologize for being wordy. 
Good Luck.    
It is not magic, just mysterious at first. 

Glen Ellis, Memphis, TN
[/SIZE]

---

