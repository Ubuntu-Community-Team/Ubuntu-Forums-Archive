---
title: "Driver issue after update"
date: 2010-03-16
forum: General Help
---

### Post by slylock on 2010-03-16
I installed Ubuntu 9.10 today on my PC. Everything worked fine after the initial install. I ran the update manager and downloaded and installed the latests ?kernel? and such. (excuse me if I am wrong but I am a Linux newbie) 

After I restarted my PC the following things stopped working (they where working just fine before) 

My 3G Huawei Thumb drive modem is recognized as a CD ROM
My audio driver is not working

I am not sure what else is not working.

I would just completely reinstall but first that wouldn't solve my ignorance of the issue and secondly I have transferred all of my files over.

I am looking particularly for help in solving this issue (getting the things to work correctly) or reverting back to before the update.

Thanks in advance.

Not sure if you want this info but here it is.

Dual core 2.6ghz
2 gigs RAM 
MSi G31TM-P31 mother board with the built in sound and graphic card

Thanks!

---

### Post by slylock on 2010-03-16
Well to make this thread more interesting so that I may get some help....IT MAKES MY TV BURST INTO FLAMES>>>>HELP....anyway folks please give me some help...

---

### Post by howefield on 2010-03-16
Have you tried starting with the previous (working) kernel ?

---

### Post by 3rdalbum on 2010-03-16
1. Those modems pretend to be a CD-ROM drive containing Windows software (then when the software is installed on Windows, the Windows driver automatically 'ejects' the 'CD-ROM' whenever it is plugged in).

The Network Manager should still be able to use the modem side even when the 'CD-ROM' is mounted. If not, then try 'ejecting' it (don't "Safely Remove", just "Eject"). Network Manager is in your top panel; right-click it and choose "Edit Connections", and then go to the Mobile Broadband tab and add a new connection.

2. In a terminal (Applications > Accessories > Terminal) type:

```
alsamixer
```

Make sure that the Master, PCM, and Front channels are turned up. In the volume control applet on your panel, make sure that your internal sound is selected as the active device in the Hardware tab.

---

### Post by slylock on 2010-03-16
mount: special device /dev/scd1 does not exist

The name of the icon: cdrom1 

That's the msg I get when ever I try and do anything with the icon. It used to show itself (the device) on the desk top as "Maxis Broadband" whenever inserted to the PC. Also when ever I try to edit or access the network connection it prompts me for my password then tells me access denied. I deleted that connection and created a new one, which of course is not working as the modem is not detected. 

I played around and got the sound to work. Ok guys lay it on me! 

Yes I tried restarting and using the old Kernel but to no avail...:(

---

### Post by slylock on 2010-03-16
OK, I just noticed that if I remove the modem the cdrom1 stays under "computer". But when the thumb drive is inserted there is another volume named: HUAWEI SD Storage. And that removes itself when the thumbdrive is removed.

There is no option to remove, unmount cdrom1.... I am perplexed. If I was in windows I would just unistall the driver then reinstall and should work well then. But here I am sooo lost.

---

### Post by slylock on 2010-03-16
As you can see, even my thumbdrive is not working well. I deleted all of the files on it and the system did not recognize that it was empty. Even after I removed it and reinserted. Then I formatted the thumbdrive as New Volume the system still showed its old name (you'll see it as SBA) there is something wrong with the Kernel that I updated. Please assist me on removing .20 and go back to .14

Thanks

---

### Post by mkp123 on 2010-05-12
[COLOR=black]This is an issue that arises after the updating of an operating system. This issue is very common to all operating systems. After the updating of an operating system the system goes restarting and after it the working of some of the drivers is completely stops. After the removal of the updates the drivers works exactly just before. This problem leads to prevent installation of operating system updates. The prevention of updating the operating system affects the performance of the operating system.[/COLOR][COLOR=black][FONT=&quot] [/FONT][/COLOR]

---

