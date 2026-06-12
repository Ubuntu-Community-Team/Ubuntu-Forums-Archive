---
title: "Backup to move to new partition?"
date: 2010-06-13
forum: General Help
---

### Post by whalogreg on 2010-06-13
So I've been trying to solve another problem (disk errors that MIGHT have something to do with ext4). I was wondering if there would be a possible way to backup my 10.04 install and move it to an existing, unused ext3 partition. I'm kinda stuck at the moment with my disk error problem, and figured I could waste some time to see if I could MOVE my install (as to not have to do a fresh install, re-install every application and script, and re-customizeand and move all of my media and files) onto an ext3 and completely remove the ext4. Is this just a stupid idea? Would I be able to configure everything to work with on a new sda?

---

### Post by colorlessprism on 2010-06-13
"dd" might work if partition size big enough, disk clone might work (there is one in unetbootin), but i would go with remastersys. use remasterys to backup your system. remastersys is limited by the iso format so you will need to copy your pics,videos,music, etc to an external hdd. you can use "disk usage analyzer" to tell you what your big folders are. you will need to comment out the big files in the remastersys exclusion list. remastersys will make an installable LiveCD of your current config:

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

### Post by whalogreg on 2010-06-13
Beautiful! I will def give this a shot and let you know. I just have to go get some dvd-r's now... :)

---

### Post by colorlessprism on 2010-06-13
since my netboook has no cd/dvd drive i take the iso remastersys creates and use the "USB startup disk creator". does what is says converts the iso so your computer can boot your backup from usb.

---

