---
title: "iPod Touch Won't Sync With Rhythmbox"
date: 2010-03-12
forum: General Help
---

### Post by LinuXGo on 2010-03-12
Hi, I've managed to successfully to sync my ipod touch to my desktop computer but I'm not able to add no music inside the device with Rythmbox. I've searched online and I've come across a online tutorial discussing about the steps required to successfully sync your ipod. In my standard, the steps is quite confusing due to lack of explaination and I'm not able to complete the task so the issue was when I'm trying to prepare the itunes directory using the mkdir command. The terminal replied back with "no file or directory exist", I thought I had selected the wrong location to begin with but then I have no idea what location is the ipod currently located.... The device appears on my computer desktop, so I typed in mkdir /Desktop/iPod_touch/iTunes_Control/Device. The device name is iPod touch so there won't be an issue with the name and I also checked the folders stored in the iPod, it contained s Sys-extended-info but its an afc file, which limit my access. I've requested assistance on Ubuntu Geek Forum but all I receive was users who are displaying thier happiness when this tutorial works for them so this isn't my first time requesting for this kind of matter. Anyone supposely offer any kind of advice to this situation?

---

### Post by ubudog on 2010-03-14
Copy all the music on the IPOD touch into your music folder.  Then, open rythmbox, go to Edit>Preferences>Music and check the box that says "Watch my library for new files"  All of your music will then be loaded into rythmbox. ;)

---

### Post by LinuXGo on 2010-03-14
Thanks for your reply, but the question that I'm currently asking doesn't seem to work with your suggested mehod. One reason is that my ipod touch doesn't contain any music files because I'm currently having issues syncing my device to the program (Rhythmbox). Another reason is that an itune directory hasn't been established which leads to my problem, since I haven't complete following the procedure as describled from my previous post. Also when I browse the device on my operating system, the music folder contains a myriad of other folders that named with letters and numbers.

---

### Post by colobix on 2010-03-14
And you don't have windows nor a windows pc near you?
You said you have access to your ipod which I don't believe, befcause if your ipod is jailbreaken you should be able to put your music onto your ipod.
Do you know what software version it has installed?
YOu should be able to jailbreak it with ubuntu if the version is older then 1.3.0. 
But for 1.3.0 or higher you have to use windows.

---

### Post by LinuXGo on 2010-03-16
Okay, I can accept your agrument but my ipod touch isn't jailbroken and yes, its true that I can access the file system if I'm not mistaken. The ipod device is mounted and it appears as two media: camera, ipod. There're websites that listed the instructions that you can successfully sync your ipod touch over a usb with or without a jailbroken ipod touch and I've seen comments that said that its had been tested with, the operation was a success. However some of us is confused with the steps and require assistance over the issue of procedure. I don't have a windows PC nor do I own one, my relative is currently using the other laptop that do have Windows installed but they're busy using it. 
 
Again, the problem with the issue of syncing the media device is clearly obvious, there're steps that only requires you to install relevant packages and editing the config files for ifuse, rebooting, mounting procedures. Then you could add music using Rhythmbox or drag/drop using nautilus and then there're some other steps that manifested more operations such as creating itunes directory and UUID.
 
If anyone wish to reply to this reply, then please do so and if you disagree with any statements that I made then please give me your point of perspective. Thanks.
 
_Note:_ My ipod touch 3G is running 3.0 firmware version

---

### Post by Yura101 on 2010-09-22
Haha well I'm sitting here reading this and then take a look at my Ipod and it syncs by it self? about 10 minutes after I plugged it in. it keeps doing it every 10 minutes or so ? I guess if you play a a song it will sync because that's what I did.

---

### Post by Yura101 on 2010-09-22
well I'm sitting here reading this and then take a look at my Ipod and  it syncs by it self? about 10 minutes after I plugged it in. it keeps  doing it every 10 minutes or so ? I guess if you play a  song it will  sync because that's what I did.

  on this post  you can download itunes version 7.6 ( because other versions don't work for some reason) I think and  you need wine to use it but it won't sync for reasons I'm not aware of.

---

### Post by gilbertoiki2 on 2011-01-10
> **ubudog said:**
> Copy all the music on the IPOD touch into your music folder. Then, open rythmbox, go to Edit>Preferences>Music and check the box that says "Watch my library for new files" All of your [[COLOR=#000000]music[/COLOR]](http://www.changeformat.net/change-avi-format/change-avi-to-zen-vision-m.html) will then be loaded into rythmbox. Thanks for your explanation! It's helpful to me, It's comprehensive.

---

### Post by hte333 on 2011-01-14
This worked for me, I was able to mount my iPod touch 2G but Rythmbox  would give an error when I tried to add files. Go to your home folder,  press CTRL+H, navigate to .gconf/apps/rythmbox/. Delete the %gconf.xml  file. restart rythmbox.

---

