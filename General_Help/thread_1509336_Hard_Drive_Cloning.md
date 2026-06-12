---
title: "Hard Drive Cloning"
date: 2010-06-14
forum: General Help
---

### Post by ITidiot on 2010-06-14
I've been recently impressed with Ubuntu which I used to recover a broken USB drive and now I'm going to attempt to use the dd command to clone my laptop hdd to a new larger capacity hdd.
 
I've read the various posts on the subject and understand the risks involved in using this command. 
 
My questions are:
 
1.  Will this work with a laptop since my new hdd will be connected via usb?
 
2.  Should the new hdd be formatted first or can it be unformatted?
 
3.  is it better to copy sda to sdb all at once or to do each partition in turn; sda1 to sdb1...etc?
 
I'm using Ubuntu netbook edition booted from a live CD.
 
Thanks in advance

---

### Post by amedac on 2010-06-14
Simpler solution:

1. install remastersys [http://www.geekconnection.org/remastersys/ubuntu.html]("http://www.geekconnection.org/remastersys/ubuntu.html")

2. Go to System -> Administration -> Remastersys backup

3. Select first option: backup -> this will backup your distribution with all installed programs and user data

---

### Post by john newbuntu on 2010-06-14
All at once clones the partition table as well as the data. This way, your size on your destination drive would be same as the source.  But if your destination drive is bigger, you will later have to play with resizing paritions around until the full drive is used (if necessary).

Doing it partition by partition gives you the flexibility to move data across partitions.  Eg: move /dev/sda1 to /dev/sdb3 etc plus use the extra space if necessary.  You could even exclude partitions. You however need to partition the destitination drive if doing it partition by partition.

Clonezilla is a tool on my USB that I have used several times to copy partitions. It creates images using only blocks that have data on them.  On restoring the image, it even copies the MBR and adjusts /etc/fstab(the UUIDs) for linux systems.

---

### Post by colorlessprism on 2010-06-14
+1 remastersys. somthing to keep ion mind though, remastersys is limited by the iso format so you will need to copy your pics,videos,music, etc to an external hdd/usb. you can use "disk usage analyzer" to tell you what your big folders are. you will need to comment out the big directories in the remastersys exclusion list (for me it is music, videos, etc). running the remastersys "backup" option will make an iso of your current config:

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

Instructions:
After you install remasterys you should open the GUI and modify the settings or you can gedit /etc/remastersys. The menu/file is pretty self explanatory. You will want to run Ubuntu's "Disk Usage Analyzer" (it should be under accessories) this will tell you what folders take up the most space. i have added my Documents, Music, Videos, Pictures, .wine, and VirtualBox to the exclusion list inside the remasterys config. I back these up seperatly using another program that does incremental scheduled backups.

When you run Remastersys, it will create an ISO image based on your current install, any programs, downloads, etc will be on the CD as well. so it may be a good time to do some house cleaning before you start.
Before you run remastersys, close every other application you are running this really can affect the build. There are two ways you can run it. To back up everything, including user's directories, click "Backup" from the remastersys window or run the following in a terminal
sudo remastersys backup

If you want to give copies of this to other people. Maybe you set it up for people who have never used ubuntu and you've made a simple setup with common programs installed, you will need to click the "Dist" option in the menus instead or you can run this command in a terminal to create a distributable version which you can give to others:
sudo remastersys dist

This will take some time, especially if you have a lot of applications installed. Once the process has finished, you can go to /home/remastersys. Inside you'll find your ISO. Move the ISO to your home directory. Make sure you grab the m5d checksum.
Now you can clear up the build directory. This is easy, just enter the following in the terminal:
sudo remastersys clean

Make sure you've moved the ISO to your home folder before you do this.

You may get an error that the image is too big to complete. this means you should exclude another folder. Once you get the hang of it, you'll have a tough time finding a better alternative

here is a link to a picture tutorial for better clarification:
[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

---

### Post by ITidiot on 2010-06-14
Thanks for your replies.  I'll try 'dd' first.

---

