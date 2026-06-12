---
title: "How to create a custom live cd?"
date: 2010-06-11
forum: General Help
---

### Post by X-Windows on 2010-06-11
I'm sure this is possible to do, but how do I create a Ubuntu install cd that uses my current config. Ideally I would like to be able to install exactly what I have on my system now, without user files. Wine, Ccsm, amarok, audacity, themes the whole nine yards. I tried using a program called Ubuntu Customization Kit, but it wouldnt let me mount the normal ubuntu install .iso file. This would avoid the hour and a half post-install config every time I screw Ubuntu up as well as stripping off many of the programs I don't need...

---

### Post by colorlessprism on 2010-06-11
remastersys is exactly what your are looking for. i use remasterys to backup my system and "back in time" to augment the iso limitations. if you have a lot of media you will need to comment out the big files (for me its places like "music" or "documents", hence the back in time). remastersys will make an installable LiveCD of your current config:

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

---

### Post by X-Windows on 2010-06-11
Is there a tutorial/howto somewhere that explains how to use remastersys to make a cd? I just recently tried it and fubar'd my hard drive. I started out with 10GB used, and it filled my partition to 100+Gb! I am a little leery of using it again, but if there is no other way...

---

### Post by colorlessprism on 2010-06-11
Im not really sure what happened. After you install remasterys you should open the GUI and modify the settings or you can gedit /etc/remastersys. The menu/file is pretty self explanatory. You will want to run Ubuntu's "Disk Usage Analyzer" (it should be under accessories) this will tell you what folders take up the most space. i have added my Documents, Music, Videos, Pictures, .wine, and VirtualBox to the exclusion list inside the remasterys config. I back these up seperatly using another program that does incremental scheduled backups.

When you run Remastersys, it will create an ISO image based on your current install, any programs, downloads, etc will be on the CD as well. so it may be a good time to do some house cleaning before you start.
Before you run remastersys, close every other application you are running this really can affect the build. There are two ways you can run it. To back up everything, including user's directories,  click "Backup" from the remastersys window or run the following in a terminal
sudo remastersys backup

If you want to give copies of this to other people. Maybe you set it up for people who have never used ubuntu and you've made a simple setup with common programs installed, you will need to click the "Dist" option in the menus instead or you can run this command in a terminal to create a distributable version which you can give to others:
sudo remastersys dist

This will take some time, especially if you have a lot of applications installed. Once the process has finished, you can go to /home/remastersys. Inside you'll find your ISO. Move the ISO to your home directory. Make sure you grab the m5d checksum.
Now you can clear up the build directory. This is easy, just enter the following in the terminal:
sudo remastersys clean

*Make sure you've moved the ISO to your home folder before you do this.*

You may get an error that the image is too big to complete. this means you should exclude another folder. Once you get the hang of it, you'll have a tough time finding a better alternative


here is a link to a tutorial you asked for:
[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

---

