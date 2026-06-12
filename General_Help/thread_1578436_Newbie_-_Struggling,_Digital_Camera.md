---
title: "Newbie - Struggling, Digital Camera"
date: 2010-09-20
forum: General Help
---

### Post by Quarkrad on 2010-09-20
Ubuntu 10.04.  In order to get my photo application (digikam 1.2) to download photos off my digital camera/SD card I have had to configure Ubuntu not to 'mount' the usb connected camera when it is plugged into the pc.  This is great - I can use digikam to download pictures off the camera/SD card into the pc.  I'm having a problem when it comes to deleting the original pictures off the sd card/camera.  Googling this problem it seems the issue is around Ubuntu only having read access to the SD card.  It appears in windows world when an sd card is presented one has read/write access so things tend to 'work out of the box'.  In Linux/Ubuntu world I'm reading that digital cameras/SD cards do not (always?) work out of the box because you only have read access.  If I close down digikam and launch nautilus I can see the camera/SD card but cannot write to it - I'm told I only have read access.  I need some help - I have also convinced my father-in-law to switch to Ubuntu but at the moment although he can download photos and view them I see no way of (ideally through digikam) of deleting the pictures off his camera/SD card.  Help.

---

### Post by Quarkrad on 2010-09-22
My father-in-laws pc is remote so when I got home I decided to set up the same scenario on my wifes pc - although with a different camera.  (I had installed a clean version of 10.04 on both machines some weeks ago).  Interestingly everything 'worked out of the box'. So now I'm thinking about the this issue of addressing/reading USB connected camera/SD cards.  On my father-in-laws pc it 'sees' the SD card as read only - where as my wifes machines 'sees' the card as read/write.  I don't really understand why as they were both installed from the same CD.  There must be some config setting somewhere.  How can I see what Ubuntu is going to do (in terms of read/write permissions) if a camera/SD card was ever connected via USB?

---

### Post by mastablasta on 2010-09-22
perhaps your father-in-law is not set as user with the privilege to write on mounted media? Check the user settings.
 
btw i never use any programmes to arrange my camera pics and videos. in windows you can use explorer, or i use total commander for all file management. in linux i usually use nautilus.
 
usually there is no need for any additional programmes after all accessing camera is just like accessing external disk.

---

### Post by coffeecat on 2010-09-22
An SD card is usually formatted FAT16 or FAT32 and Ubuntu should automount that read/write by default. 

> **Quarkrad said:**
>   Googling this problem it seems the issue is around Ubuntu only having read access to the SD card.  It appears in windows world when an sd card is presented one has read/write access so things tend to 'work out of the box'.  In Linux/Ubuntu world I'm reading that digital cameras/SD cards do not (always?) work out of the box because you only have read access.

It sounds as though the Google hits you found are highly misleading. I've heard of cases where a USB device formatted FAT is mounted read only, but this must be a misconfiguration in the installation or some really obscure problem.

Anyway, mastablasta makes a good point. But if you find that your father-in-law's account is set to access external storage in the Users configuration, try booting up with a live CD and seeing if you can access the card read-write in the live session. If you can't, that might suggest some obscure hardware problem, or...

It sounds as though you are plugging in the whole camera via USB. If you are and the problem persists, have you tried removing the card and using a USB card reader? If you don't have one, you can get a cheap one from Amazon. Example from Amazon UK:

[http://www.amazon.co.uk/Integral-USB-Single-Slot-Reader/dp/B000VY80AM/ref=sr_1_1?ie=UTF8&s=computers&qid=1285145801&sr=8-1](http://www.amazon.co.uk/Integral-USB-Single-Slot-Reader/dp/B000VY80AM/ref=sr_1_1?ie=UTF8&s=computers&qid=1285145801&sr=8-1)

I'm sure there's something similar in an Amazon near you. I've got one like that which came "free" with an SD card. Very useful.

---

### Post by Quarkrad on 2010-09-22
Thanks - father-in-law is 80 miles away so this could take time (re live cd) although I do have remote desktop access.  sorry for simple question but how do I check his user privilege is set to write on mouned media?  (By the way, if I close down the app (digikam) and look at his camera through Nautilus I ca see his camera, double click and see his SD card and the pictures on it.  If I try to delete them (as you would in winworld/explorer) I'm told I do not have write access.  The odd thing is, on my wife's PC, Nautilus and digikam will let me delete files off the sd card in the camera).

---

### Post by coffeecat on 2010-09-22
> **Quarkrad said:**
> Thanks - father-in-law is 80 miles away so this could take time (re live cd) although I do have remote desktop access.

Is it only with remote access that you get the read only problem? I mean, have you tried this when you are physically at your father-in-law's machine? It sounds as though you have but I was wondering if it's the remote access that's causing the problem.

Anyway...

> **Quarkrad said:**
>  sorry for simple question but how do I check his user privilege is set to write on mouned media?

System > Administration > Users and Groups. Highlight your father-in-law's account if there is more than one, then Advanced Settings button > User Privileges tab > check that 'access external storage devices automatically' is ticked. Although, come to think of it, if that was unchecked I would have thought that nothing would automount at all, even read-only. You'll need administrative privileges to get into advanced settings.

---

### Post by Quarkrad on 2010-09-22
Sorry - a little more detail.   I converted my father-in-law to Ubuntu 10.04 a week ago down on the South Coast.  The only slight issue was his photo software. He is in his 80's and it is difficult to change - on his win machine I installed a photo album package many years ago called Coral Photo Album 6.  Last weekend I install digikam because of all the Linux packages digikam 'looks' very much like Coral and he can use it without much trouble - so the Ubuntu installation has been very successful.  The only issue is he cannot use digikam to delete pictures off his camera (actually the SD card in the camera) once he has transferred them to his pc. On Sunday I keep getting the message that I had no write access.  So I closed digikam and looked a the camera/card via Nautilus - same thing - could not delete pictures off the card.  I had to post something on this forum for help.

Yesterday at home I connected my wifes camera (different to my father-in-laws) to Ubuntu 10.04/digikam to have a play with this 'write' issue but to my surprise everything worked OK - on her machine she has read/write access to her camera/card via the digikmam app or Nautilus.


I looked in her Users and Groups and YES she has 'access external storage devices automatically' ticked.  I just phoned my father-in-law and connected to him remotely and looked at his settings.  He too has 'access external storage devices automatically' ticked.  

So it looks that although both machines have 'access external storage devices automatically' ticked my wife has read/write access but my father-in-law only has read access.  (I installed 10.04 on both pcs from the same live CD - they are only used for basic web access and mail - I have not configured anything 'under the bonnet'.

---

### Post by coffeecat on 2010-09-22
Thanks for clarifying things. I think I get the picture now.

Tbh, I wasn't surprised that the setting in Users and Groups was already ticked. Anyway, let's delve a little deeper. First of all, plug a camera in to your wife's Ubuntu (the one that's working as it should) and let it be mounted. Now navigate to the file /etc/mtab. If you double-click on it, it will open in the gedit text editor read only. That's OK - it's a system file and shouldn't be tampered with. We only want to look at it. At the end you should have a line something like:

```
/dev/sde1 /media/FC30-3DA9 vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0
```That's what I get with my camera. It will probably wrap over more than a line in the text editor window but it is just one line. The first field "dev/sde1" in mine may appear as /dev/sdb1 or /dev/sdc1 depending on how many hard discs and other devices you have in your machine. And /media/FC30-3DA9 will appear as /media/somethingelse. The third field - vfat - is the filesystem type. But the fourth field - all that gobbledegook - is what we want. You can copy and paste that text into another tab or window of the text editor to save it if you want. You'll see that the fourth field starts "rw" - that means read-write.

Now get your father-in-law to plug his camera in and then look at the last line in his /etc/mtab. See if they are the same (in the fourth field - differences in fields one and two don't matter). If you could post both, that would be helpful.

Either we'll see that the mount options with your father-in-law's machine are different, and then we can look at the udev rules. I think this is unlikely and, besides, I'm a bit shaky on udev rules, but I don't mind investigating. 

**Or** we'll see that the lines are the same. In which case I haven't a clue what to do, except to make this comment. I have noticed, but only occasionally, threads like yours where the OP cannot write to an automounted FAT-formatted USB drive. This is not expected behaviour. Your wife's Ubuntu is behaving as it should - read-write for automounted USB drives. These threads are not common - perhaps they are the basis for the google hits you found - but clearly there must be an obscure bug affecting some. Perhaps your father-in-law's hardware is susceptible to this bug, if bug it is. In which case the only thing I can suggest is that he deletes unwanted photos using the camera. Not exactly convenient, I admit.

And my suggestion of the USB SD reader was probably not a good one considering his age. I guess his fingers may not be as nimble as they once were and getting an SD card in and out of a camera may be too fiddly. Besides, this read-only issue might not be solved using this.

---

### Post by VanillaMozilla on 2010-09-22
If I can make a suggestion, I know this isn't what you asked for, but reading those cards directly from the camera can be problematic.  Usually the camera _should_ look like any other USB storage device, which you can read and write to.  Ideally, this should work fine, but I typically encounter performance problems, such as, the camera shutting off while transferring files.  And I'm not a fan of having to use special software to read the card.  Software is generally pretty buggy, and you're at the mercy of the quirks of that software.

You may want to consider buying a card reader.  That may save you a lot of troubleshooting, and at a minimum it will save your camera batteries for better use.

Unfortunately, a lot of card readers -- even major brands -- are also problematic.  For myself, I just threw away my pile of cheap ones and finally went to newegg.com and bought a good one.  I looked for one that would read almost any kind of card, and I checked the user reviews to find one that almost NO ONE had any problems with.  I think it cost me over $30, but it was the easiest troubleshooting I ever did.

---

### Post by Quarkrad on 2010-09-23
Sorry for the delay - father-in-laws email system packed up and I had to sort out remotely.  NTLworld.com migrating to Virgin media servers Arrrrrr.  Anyway - here is the output you asked for:

**Wife**
/dev/sdc1 /media/38D0-47DC vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0

**Father-in-Law**
/dev/sda7 / ext4 rw 0 0
none /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sda5 /media/6A18616E18613A69 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda5 /media/6A18616E18613A69_ fuseblk rw,noexec,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda1 /media/</media/sda1/> fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
/dev/sda6 /media/Images fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/tony/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=tony 0 0

I included more info on father-in-laws output.  I looks to me he has rw access but further along the line it also says permissions 0 0.  My wife's 'last line' was rather short - similar to yours.

---

### Post by Quarkrad on 2010-09-23
VanillaMozilla - thanks for your reply; I agree with all you say.  Unfortunately, I'm finding out that when you are 80 even getting an SD card out of a camera is not easy.  If we could get this to work (as it does on my wife's set up) it would be off great benefit. Transferring pictures to and from camera to pc is hard enough - having other things in between like card readers is another (major) step.

---

### Post by coffeecat on 2010-09-23
It looks to me that the camera was not plugged in (or switched on) to your father-in-law's computer. There is no vfat line at all. If you are referring to the /dev/sda6 line when you mention rw access, then no, that's partition #6 on the main hard drive. Or if you mean the binfmt_misc line, that's part of the system. I've got that too. **Edit:** neither the last line - gvfs-fuse-daemon. That's normal too, part of the system. **End edit**

Quick explanation of drive naming: sda is your main hard drive, sda1 being partition 1. sdb, sdc, sdd, etc are any subsequent drives whether conventional SATA, PATA or SCSI drives, usb drives, SD cards and so on. The reason that my camera came up as sde1 is that I have two internal SATA drives, sda and sdb and an internal card reader with two slots which appears as sdc and sdd whether or not there is a card in it.

Also - those two zeroes are nothing to do with permissions. They are the dump and pass fields which are something else altogether.

I think the most likely explanation is that the camera wasn't switched on. If a mount line doesn't appear in mtab, then the device hasn't been mounted and you wouldn't be able to access it read-only let alone read-write. Either that or there is something seriously weird with the system.

---

### Post by jwbrase on 2010-09-23
Other than the issue of whether the camera is switched on, there's also the issue of possible differences between the two models of camera. My own camera starts to get finicky if I delete files off of it with anything other than the camera's own interface.

---

### Post by Quarkrad on 2010-09-23
OK - remotely logged on and sat (virtually) with him. Desktop -camera plugged in and switched on.  Launched nautilus and saw camera icon labeled as USB PTP - it was not mounted as I configured it this way following previous google recommendation re digikam connected USB cameras.  Although not mounted mtab output was largely as before;

**Unmounted**
/dev/sda7 / ext4 rw 0 0
none /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sda1 /media/</media/sda1/> fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
/dev/sda6 /media/Images fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
/dev/sda5 /media/6A18616E18613A69 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda5 /media/6A18616E18613A69_ fuseblk rw,noexec,nosuid,nodev,allow_other,blksize=4096 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/tony/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=tony 0 0

I then went into nautilus and mounted the camera. The mtab output was the same:

**Mounted**
/dev/sda7 / ext4 rw 0 0
none /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sda1 /media/</media/sda1/> fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
/dev/sda6 /media/Images fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
/dev/sda5 /media/6A18616E18613A69 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda5 /media/6A18616E18613A69_ fuseblk rw,noexec,nosuid,nodev,allow_other,blksize=4096 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/tony/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=tony 0 0


I fear that perhaps although I mounted the camera it did not change mtab because I may have had to do something else.  I was expecting to see a change in mtab.

---

### Post by VanillaMozilla on 2010-09-23
> **Quarkrad said:**
> VanillaMozilla - thanks for your reply; I agree with all you say.  Unfortunately, I'm finding out that when you are 80 even getting an SD card out of a camera is not easy.  If we could get this to work (as it does on my wife's set up) it would be off great benefit. Transferring pictures to and from camera to pc is hard enough - having other things in between like card readers is another (major) step.
It's very easy, really.  The card is probably spring-loaded.  Just push it in, then release it, and it should pop part of the way out.  If you ask me, I'd say it's a lot easier than trying to configure your computer.

When you put the card back in or put it into another device, if it doesn't go, try turning it over.  Putting it into the camera again, you'll probably have to push it again until it clicks or won't go any further.  You should be able to tell easily.

Be sure not to get it dirty, and keep your fingers off the contacts, and you shouldn't have any problem.

---

### Post by coffeecat on 2010-09-23
> **Quarkrad said:**
> I was expecting to see a change in mtab.

So was I. :(

To go back to your original post...

> **Quarkrad said:**
> Ubuntu 10.04.  In order to get my photo application (digikam 1.2) to download photos off my digital camera/SD card I have had to configure Ubuntu not to 'mount' the usb connected camera when it is plugged into the pc.

What was the 'configuration' that you did? I didn't understand this bit. Normally you let the desktop automount the camera whether or not you are using a photo-managment app or simply using a file browser like Nautilus. Do you mean that digikam wouldn't download photos if the device was automounted? That's very odd.

---

### Post by Quarkrad on 2010-09-23
I cannot find the original post that suggested (in order to get digikam to operate) it was best to not have the camera mounted when it was plugged in.  Looking back it was probably not a good idea.  I just plugged my wife's camera into her PC and noted that it is mounted - all rw features work so I think the best thing is for me to draw a line in the sand at this point. We are going down to the South Coast next week so rather than speculate/remote connect I think I will take my wife's camera down and test. It could even be how his SD is formatted but I suspect not.  These are both modern compact cameras so they should be similar.  Mother-in-law also has a different camera so I will have combinations of 3 cameras/SD cards to play with.  If it ok with you I will come back after some more 'hands on' playing.

---

### Post by coffeecat on 2010-09-23
> **Quarkrad said:**
> If it ok with you I will come back after some more 'hands on' playing.

That's fine. I'm subscribed to this thread so as soon as you post I'll get a notification. I'll be interested in what you find. 

Good luck!

---

### Post by Quarkrad on 2010-10-16
I'm not sure why but all works now(?).  Recent visit armed with three different digital cameras to test proved to be wasted as all functions, including reading and deleting to SD card were perfect.  Thank you very much for your support with this issue and the various fixes I put in place along the way.

---

