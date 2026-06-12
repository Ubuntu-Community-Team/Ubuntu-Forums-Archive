---
title: "network icon gone"
date: 2010-04-28
forum: General Help
---

### Post by mallorcaben on 2010-04-28
Thinkpad T41 1 gig
Ubuntu 9.10

Hi, Ive had a few freeze ups on this system but the last time it affected the top panel.
The wireless icon has disappeared to be replaced by an extra bluetooth icon.
screenshot attached.

Im new to Linux although a very experienced Windows user.
Is there any kind of clean up utility (like tune up utilities in win)

Also, any kind of log so I can trace this freeze up I&#7743; getting.
Ive only just got this laptop so dont know if it did it before although prev owner never mentioned it.

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
You may want to focus more on the freezing issue. That could resolve most other issues you may be having. Is your networking affected? If so you can restart it: ```
sudo /etc/init.d/networking restart
``` If it's just the applet you can ```
killall nm-applet && nm-applet
```

---

### Post by mallorcaben on 2010-04-28
its the whole laptop thats freezing up. Random times. 
Ive just rebooted from another freeze.
The wireless icon is still gone but now I have 2 sound icons!
very odd

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
To get the icon back execute the second command I gave you. You can copy and paste it and it should restore the network manager applet. whatever is causing the computer to freeze is probably the cause of the problem with your applet. If you're pressing the power button to turn it off after it freezes you might want to know that that can corrupt your hard drive. Either try to get a CLI (ctrl+alt+F1) and restart gdm (sudo service gdm restart) or if you can't get the CLI then on the right side of the keyboard hold ctrl+alt+SysRq and while holding them type REISUB one by one. SysRq is also the print screen button up by scroll lock. Also have a look at your log files by going to System>Administration>Log File Viewer and looking into the dmesg and kern logs. They may have relevant information to the cause of your freezes. If you see anything with an EE or WW or error in it then you should google that to try and find a solution. An easy way to find errors in a log is to use the ctrl+f search function to find specific words or whatever.

---

### Post by neur0 on 2010-04-28
First thing you need to do is to find out what is causing your Laptop to freeze.
Make a new user account, log on with that user and see if the new user has the same problem with the missing network icon if you can't get it back any other way.

Install lm-sensors ([https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)) and check out the temperatures.

Run memtest for a couple of hours and see if there are errors. (It should be available as an option in the GRUB menu during booting)

Check the hard disk for errors 
The easiest way to do this is to run 
```
sudo fdisk -l
```
in the console to see what disk devices you have on the system
Note the one(s) that have the "Linux" label in the "System" tab
For example: /dev/hda1 or /dev/sda1 etc. (It should be one of these on a laptop)
then run
```
sudo tune2fs -c 1 /dev/hda1
```
replacing /dev/hda1 with whatever device you found in the table from the fdisk -l command which has the "Linux" label in the "System" column.
If you have more then one disks with the "Linux" label, just repeat the tune2fs command replacing /dev/hda1 with other devices you found.
Reboot and wait for the checks to finish
Run the tune2fs line again for all the devices you set and change the "-c 1" part to "-c 50"

Note: With "-c 1" you set the auto file system check feature to check the file systems on every boot. With "-c 50" you change them to check every 50 boots. You can always skip the file system checks with [Esc] button.

---

