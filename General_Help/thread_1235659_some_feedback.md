---
title: "some feedback"
date: 2009-08-09
forum: General Help
---

### Post by gaastra on 2009-08-09
Im a beginner. and I do not know what im doing, my first time using ubuntu. And since i do not know where to post this, ill post this hire.

ubuntu live CD I downloaded today and tried it to recover some files from NTFS HDD.

2 GB ram 2 sticks in dual channel mode i think + reader s.exe infected Hard drive (you know the one that wont be removed even after you format your hard drive....)

after using it for couple hours I got some issues.

First I started it up in try me mode and recovered some files and. all was good, it detected all my usb sticks and hard drived and USB hard drives.

Connecting my adsl was kind of tricky, cuz the help file was not that helpful, it said use the config manager, but it did not say where on earth is it. ( it was in the right top corner....)

after i inserted my user and pass nothing happened, but after I tried again after couple minutes the (DSL connection 1) did appear after clicking on the icon in the right top corner. 

And yes it connected sucessfully.


Now to the buggy part. 

1) Ubuntu runs in the ram right? why its so slow? The thing that tickked me off the most was the lag, i mean ubuntu lags a lot and it freezes. like windows, only more often.

2) another thing is that the firefox i used stopped responding, it happened often. Yes ubuntu stops responding for couple seconds wery often

3) As I said I was copying files and browsing internet with firefox. while copying file ubuntu was performing wery slow. I mean you cant do anything while its copying files. wery annoying.

4) While copying files it was able to copy around 30 GB and then it crashed, it happened around 3 times, the screen goes black  and it turns off the computer or it simply goes black or shows this error message>  [http://i29.tinypic.com/206dm2v.jpg](http://i29.tinypic.com/206dm2v.jpg)

5) if the computer freezes, well i can move the windows, but nothing responds and if I hit restart it showed me this error message again, see the pit above.

6) I dunno what it is, maybe I have a virus in my ram and its interfering with ubuntu, bites me.

7) Another thing, i tried to enter the GUI to format my Hard drive, gparted thing and it said it is lockked or used by someone else.  i think i typed **sudo gparted** i dunno maybe i did it wrong.

8) why does my CD in the CD rom constantly spins? I mean the os should be running in ram why is it spinning. (I mean I dot 2 Gigs, use it, ..no?)

k i think this is it for now. Hope this helps you make it better.

---

### Post by snowpine on 2009-08-09
Hi Gaastra, welcome to the forums!

The Ubuntu Live CD does not run from ram; it will constantly access the CD and run very slow. This is totally normal. Ubuntu will run much faster once you install it.

You mention that you're having problems/crashes with both Windows and Ubuntu. This points towards some kind of hardware problem. A good place to start is to run the memory test utility from the Ubuntu Live CD. 

ps 'gksu gparted' is preferable to 'sudo gparted'--sudo is for command line apps and gksu is for graphical apps like gparted.

---

### Post by Barafu Albino Cheetah on 2009-08-09
1) You have run in "try me" mode? Of cause it is slow and buggy. Any liveCD is slow. And uses the disk. And freezes.  
Install ubuntu on your disk, and install proper drivers, and see speeeeed and stability. 
2) There can be no virus that survives formatting.

---

### Post by gaastra on 2009-08-09
> **Barafu Albino Cheetah said:**
> 1) You have run in "try me" mode? Of cause it is slow and buggy. Any liveCD is slow. And uses the disk. And freezes.  
Install ubuntu on your disk, and install proper drivers, and see speeeeed and stability. 
2) There can be no virus that survives formatting.

There is the virus im infected, it survived formating>  **Reader_s.exe (Reader_s)**

[http://www.virusremovalguru.com/?p=1511](http://www.virusremovalguru.com/?p=1511)

About crashing, my Win XP almost never crashed. So my hardware is ok.

I see why its slow, but i cant install it cuz i need to delete all partitions and format all in linux partition to gt rid of that virus.

thanx for gksu thing, ill try it.

---

### Post by snowpine on 2009-08-09
The Ubuntu installer should give you the option for guided install--use entire disk. This will delete all of your Windows partitions and install Ubuntu as the only operating system. No windows virus can survive that! :)

---

### Post by Barafu Albino Cheetah on 2009-08-09
About Reader_s - it don't survive formatting. It just infects everything and people forget to clean all the places. Install SP3 to start fighting it.

Use DrWeb CureIt LiveCD to fight the beast.

---

### Post by gaastra on 2009-08-09
I was using SP3 to begin with and i did format my partition, but the reader was back.

well anyway ill make 100% clean my hdd now.

also forgot to mention 3 more issues>

1) I cant open images, jpg files, i can see, that the img was opened for like 0.2 seconds ^ then the window is closed. this happens especially when im copying files  and ubuntu lags.

2) same thing happened with firefox, it was closed after it tried to open it.

3) network layer something cant find any resources and cant continue. then it shut down my network connection, ^ i tried to restart, but got this buffer error after i restarted pc, see the img above.

I guess ubuntu live CD does not like copying many GB of files

---

### Post by snowpine on 2009-08-09
None of the bugs you're describing are normal for Ubuntu. 

Check the integrity of your Ubuntu CD:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

And I recommend running the memory test, too. Something is wrong with either your Ubuntu disk or your hardware...

---

### Post by gaastra on 2009-08-09
> **snowpine said:**
> None of the bugs you're describing are normal for Ubuntu. 

Check the integrity of your Ubuntu CD:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

And I recommend running the memory test, too. Something is wrong with either your Ubuntu disk or your hardware...


I set my burner to vertify the cd tho. 

The integrity check failed, 1 file was broken, did not say what file. guess the CD overheat, cuz after i took it out it was really hot, almost burned my fingers. (note that its rewritable Cd with 8-12x speed)

And om out of CDs now, second CD died today. is there any easy solution that lets you run ubuntu like from CD, but just from USB stick ?

---

### Post by snowpine on 2009-08-09
Yes; unetbootin can create a `live usb`:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Very cool application.

---

### Post by gaastra on 2009-08-09
> **snowpine said:**
> Yes; unetbootin can create a `live usb`:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Very cool application.

I tried this app, formated my 2GB USB to fat 32 & used this app to make the USB install, but after i reboot:

I have 4 options: (Im using gigabyte mainboard)

USB-FDD
USB-ZIP
USB-CDROM
USB-HDD

and I get boot disk failure every time, i tried all options, does this mean i cant boot from usb ?


_**EDIT> NVM>**_

Enable legacy USB support in bios, if wont help, format usb to fat32 and whe it boots up, hit F12 ^ choose HArd Drive, then it will let you choose USB, it worked for me.

---

