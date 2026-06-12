---
title: "Need some major assistance please"
date: 2010-06-15
forum: General Help
---

### Post by bkeaver on 2010-06-15
Hi, I need some help if I can get it please. Here is what I am trying to accomplish. I need away to create either on a flash drive or cd a custom install that I can distribute to my users to work from without them being able to save anything to the media (whether it be usb or cd). I can create currently a usb flash drive but the only way to customize it is to create a persistent file or Casper-RW as its named which works for the customizing of the install but however if I would give it out to a user they can change and or add to it which I dont want them to be able to do. 

if I could create a bootable iso image of the flash drive and it works that would be good but i fall short of that everytime. I am currently playing with remastersys but havent had too much success with that too.

any suggestions or help would be greatly appreciated.


Thanks in Advance

---

### Post by yeleek on 2010-06-16
If you were to develop such a system and deploy it via CD, people couldn't write to it anyway.

Couple of recent conversations which may help
[http://ubuntuforums.org/showthread.php?t=1509468&highlight=kiosk](http://ubuntuforums.org/showthread.php?t=1509468&highlight=kiosk)
[http://ubuntuforums.org/showthread.php?t=1483019&highlight=kiosk](http://ubuntuforums.org/showthread.php?t=1483019&highlight=kiosk)

Last one should help in particular as it revolves around 'I need users to be able to use only the programs I provide, Firefox, Opera and OpenOffice. They must be able to download stuff (documents) so blocking download in the browser is not an option. '

---

### Post by colorlessprism on 2010-06-16
use remasterys. the "distro" option in remastersys should be what you need. you will need to comment out any files you do not want in your "distro" in the remastersys exclusion list. remastersys will make an installable LiveCD of your current config:

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

