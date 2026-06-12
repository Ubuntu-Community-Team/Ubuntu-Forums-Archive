---
title: "ipod touch 4g 4.2.1 sync"
date: 2010-12-28
forum: General Help
---

### Post by patmalcolm91 on 2010-12-28
I've managed to do the tethered jailbreak for my ipod touch 4g running iOS 4.2.1. I changed DBVersion in /System/Library/Lockdown/Checkpoint.xml from 5 to 2, deleted itunes_control, then plugged into itunes and added a song (to have itunes rebuild the database structure with version 2). I have the pmcenery ppa and the most up to date usbmuxd, libgpod, and libimobiledevice libraries.

When I plug in my ipod touch, it mounts fine, gtkpod, rhythmbox, and banshee all detect it and show the music on it. when trying to sync with gtkpod, it says "unsupported checksum type" (which is why i reverted the DBVersion, but the error remains despite the reversion). Rhythmbox and Banshee both seem to sync properly: files transfer to the itunes_control folder, the ipod says "sync in progress", and when I open the music player app afterwards, it says it's updating. But the newly added music doesn't appear.

Any idea either: a) why reverting the DBVersion doesn't make the checksum compatible (which i assume to be the problem) or b) when DBVersion 5 support will be added to libgpod? Any idea for a workaround until then. I will be losing access to windows computers in two weeks as i'll be heading back to school from break and it would be great if I could resolve this by then.

EDIT: even after changing the DBVersion and deleting iTunes_control, "ideviceinfo -q com.apple.mobile.iTunes -k DBVersion" still returns "5". Does something else need to be changed/deleted to force it to revert?

---

### Post by patmalcolm91 on 2010-12-30
I stumbled upon the problem. For some reason, I needed to reboot the ipod immediately after deleting iTunes_control.

---

### Post by martin.bartlett on 2011-01-17
Question - is the iPod still in "tethered jailbreak" mode - i.e. do you have to have it attached to your computer when ever you reboot it?

---

### Post by patmalcolm91 on 2011-01-17
Mine is a tethered jailbreak, yes. As far as I know, the untethered jailbreak for 4.2.1 on the iPod Touch 4G hasn't been released yet. Not sure on how long that will take.

---

### Post by RafaelL on 2011-01-23
I have the same problem with the same device. However, mine is not jailbraked - at least not until a better jailbrake comes along.
Additionally, I don't know how to revert to previous databases etc. so I am a bit further behind with this problem... :D
Nevertheless, I'm hoping that the community finds a solution soon.
I already sent an email to Apple demanding better compatibility, and that's about all I know how to do with computers... :D

---

### Post by Rosechimera on 2011-05-06
Jailbreaking seems like it would require too much upkeep and I've tried everything else I could find. The best solution I have is a work around. I installed fileviewer usb free version app from the itouch and I just click the app in ubuntu and put my music in the documents folder. Mp3's play from the app. No itunes required (although the app says it is). I'm using Natty Narwhal and my touch is 4.2.1. Prior to Natty Narwhal, I don't think my apps appeared in ubuntu when I plugged the ipod in, now they do immediately.
Here is the app's website: [http://web.me.com/mlcohen/FileViewer_USB_Free/Home.html](http://web.me.com/mlcohen/FileViewer_USB_Free/Home.html)
Good Luck

---

