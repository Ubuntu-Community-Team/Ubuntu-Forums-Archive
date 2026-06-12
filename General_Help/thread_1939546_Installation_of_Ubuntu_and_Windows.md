---
title: "Installation of Ubuntu and Windows"
date: 2012-03-11
forum: General Help
---

### Post by alextop30 on 2012-03-11
Well I have a rather specific question here which I have been unable to find the answer to on the net. I have 3 different hard drives and they are as follows:

1. 30 Gig Solidstate - Used for Windows 7
2. 300gig Sata (Installed Programs)
3. 1T Sata for storage.


I want to install Ubuntu along side Windows but on different drives. I will be working on reinstalling my entire system tomorrow and I want to some advice and how I can do the installation. I need windows to remain on the SSD as it is the "main" operating system. I actually use Ubuntu a lot since my laptop only runs Ubuntu. I want to be able to install ubuntu on the 300gig disk as a partition. The 300gig one is 7200 rpms and it is quite faster than my storage drive which should be accessible in ubuntu as well.

Is it better for me to install Ubuntu first on the partition and after run the Microsoft installation. With that I know Windows overwrites the MBR and thus I will not be able to boot through grub. 

Basically what is the best way for me to install Ubuntu so that I can get the dual boot functionality? I am not an a programmer so if you can also post some detailed steps on how to overwrite the MBR if it is necessary I would really appreciate it.


Thanks a lot 


Alex

---

### Post by Mark Phelps on 2012-03-12
What I would recommend is the following:
1) Download and burn the CD Image of the Free version of Partition Wizard (MS Windows app)
2) Boot from that cd
3) Use PW to shrink the partition(s) on the 300GB drive to make some unallocated space on the left for Ubuntu.
4) Shutdown the PC
5) Disconnect the SSD and 1TB drives
6) Boot from the Ubuntu desktop CD and install to the 500GB drive.
7) Reboot and confirm that Ubuntu boots to a desktop OK
8) Reconnect the SSD and 1TB drives -- but continue to boot from the 500GB drive
9) Once into Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the default GRUB config file.

Once you reboot, you should see a GRUB menu.

---

### Post by Paqman on 2012-03-12
If you're reinstalling Windows anyway then do that first, then when you install Ubuntu take the option of manual partitioning in the installer (called something like "do something else...") and carve out a root partition of 20GB+ and a small swap partition on your 300GB drive.

---

### Post by mastablasta on 2012-03-12
> **Mark Phelps said:**
> What I would recommend is the following:
1) Download and burn the CD Image of the Free version of Partition Wizard (MS Windows app)
2) Boot from that cd
3) Use PW to shrink the partition(s) on the 300GB drive to make some unallocated space on the left for Ubuntu.

 
 
windows disk manager should do this. you set the partitions and the repartitioning is then done before the drive is mounted i believe.

---

### Post by alextop30 on 2012-03-12
> **Mark Phelps said:**
> What I would recommend is the following:
1) Download and burn the CD Image of the Free version of Partition Wizard (MS Windows app)
2) Boot from that cd
3) Use PW to shrink the partition(s) on the 300GB drive to make some unallocated space on the left for Ubuntu.
4) Shutdown the PC
5) Disconnect the SSD and 1TB drives
6) Boot from the Ubuntu desktop CD and install to the 500GB drive.
7) Reboot and confirm that Ubuntu boots to a desktop OK
8) Reconnect the SSD and 1TB drives -- but continue to boot from the 500GB drive
9) Once into Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the default GRUB config file.

Once you reboot, you should see a GRUB menu.

Ok the only thing that I can say is wow I followed the directions with some difference of creating the partitions because I was installing windows so I just did it through the recovery console before installed windows. Now the only question that still remains in my head is what is the way to get Ubuntu to extend my desktop the way windows does because I have 2 monitors. I want the desktop extended not cloned. Currently when I get in Ubuntu my second monitor is not even on so any of you have any suggestions. 


By the way thank you all for the great advice.

---

### Post by sudodus on 2012-03-13
> **alextop30 said:**
> Ok the only thing that I can say is wow I followed the directions with some difference of creating the partitions because I was installing windows so I just did it through the recovery console before installed windows. Now the only question that still remains in my head is what is the way to get Ubuntu to extend my desktop the way windows does because I have 2 monitors. I want the desktop extended not cloned. Currently when I get in Ubuntu my second monitor is not even on so any of you have any suggestions. 


By the way thank you all for the great advice.
Are you running 'vanilla' Ubuntu 11.10 (or some other flavour, Kubuntu, Xubuntu, Lubuntu) or version for example 10.04 or 12.04-beta)? I'm asking because the advice might vary depending on flavour and version.

[I]Edit: What graphics chip or card are you using, and which graphics driver? If you post the output of the [COLOR="red"]following command[/COLOR], the answer should be there. Install if necessary
```
sudo apt-get install mesa-utils
```
```
[COLOR="Red"]glxinfo|grep -i opengl[/COLOR]
```[/I]

---

### Post by Mark Phelps on 2012-03-13
> **alextop30 said:**
> ... Now the only question that still remains in my head is what is the way to get Ubuntu to extend my desktop the way windows does because I have 2 monitors. I want the desktop extended not cloned. Currently when I get in Ubuntu my second monitor is not even on so any of you have any suggestions. 

Your original problem dealt with installation; your new one deals with multiple desktops.  These are entirely different problems.

You need to start a NEW thread dealing with the multiple monitors problem; don't just keep adding new problems onto an existing thread.

If your installation problem is now solved, then please use the thread tools at the top of the thread to mark this one as SOLVED.

thanks

---

### Post by alextop30 on 2012-03-13
> **Mark Phelps said:**
> Your original problem dealt with installation; your new one deals with multiple desktops.  These are entirely different problems.

You need to start a NEW thread dealing with the multiple monitors problem; don't just keep adding new problems onto an existing thread.

If your installation problem is now solved, then please use the thread tools at the top of the thread to mark this one as SOLVED.

thanks

10/4 I will mark this as solved and open a new one about the graphics drivers.

Thanks for the help.

---

