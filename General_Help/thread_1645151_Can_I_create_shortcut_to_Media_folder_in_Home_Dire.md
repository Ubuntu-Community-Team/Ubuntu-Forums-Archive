---
title: "Can I create shortcut to Media folder in Home Directory?"
date: 2010-12-14
forum: General Help
---

### Post by meddleuk on 2010-12-14
I currently have an ASUS eebox which is running XBMC Live which includes a stripped down version of Ubuntu. The computer will be used by various people within a teaching environment and I have successfully installed launchers for Openoffice which can be opened within XBMC.
 
I am trying to the make the experience for the end user as simple as possible as the vast majority will have never used Linux before. I want to get to a point where they can open Openoffice, plug in their USB stick and navigate quickly to their files. At the moment when the program is launched and I try and navigate for a file it automatically starts in the Home Folder of xbmc. So I have navigate up a couple of times, then find the /media directory where the USB stick has been mounted and so on. What I was hoping to do is create a shortcut within the Home Directory which takes you straight to the Media folder where usb is mounted. 
 
I have already attempted and created a folder within the Home directory and called it usbpen.
 
I have then added the following line into fstab
/media /home/xbmc/usbpen none bind 0 0
 
Now when I reboot the machine and navigate to the home/xbmc/usbpen folder I can see the Drive name of the USB device mounted in /media but I cannot navigate through any of the files, I am greeted with a read error message. So the shortcut is only allowing me to see the device name only.
 
Is there any advice anyone can offer to get this to work. Please be aware that due to running XBMC Live I do not have a Windows manager installed and therefore everything must be done through the terminal.
 
Any help would be greatly appreciated.

---

### Post by surfer on 2010-12-14
( i think the entry in your fstab should be the other way round:
```
/home/xbmc/usbpen /media none bind 0 0
```)
...sorry, that is plain wrong! your entry is ok.

and why don't you use softlinks instead?
```
$ ln -s /media /home/xbmc/usbpen
```

---

### Post by CharlesA on 2010-12-14
The fstab line looks wrong.

It's normally something like this:

```
/dev/sdxy /path/to/mountpoint filesystemtype defaults 0 0
```

See here: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by ajgreeny on 2010-12-14
I thought OOo always defaulted to the last place that a file was opened from, or saved to, when you go to File Open, certainly my system does; I have just tried it to make sure.

So if the USB disk you are using for the data files always mounts to the same place in /media, the system should go to the USB disk when you ask OOo to open a file, if that was the pathway used last time.

Does each user have their own home folder, or does everyone use the same home?  If the former, each user could label on their own USB drive partition with their username, or anything else they choose, and OOo should then go to that automatically when opening files as each use will have their own config for OOo.  If they all use the same home, all the USB drive partitions would need the same label, or there could be problems.

I think I have got this right, but would be glad to hear of any problems that arise from this suggestion.

---

### Post by meddleuk on 2010-12-15
Hi,
 
many thanks for your advice. I tried editing fstab again however I still can't get it to work. However I was able to create a shortcut "ln -s /media /home/xbmc/usbpen" so thanks for that surfer.
 
The machine will only have one username and password for all teachers and each of them will have their own memory pen or hard drive to attach. I have tested it with a few different pens and openoffice will always return to the last directory a file was opened in as long as the USB pen is still attached to the PC. If not it will default back to the Home directory.
 
Many thanks for your help

---

