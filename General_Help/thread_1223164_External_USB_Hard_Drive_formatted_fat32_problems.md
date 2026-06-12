---
title: "External USB Hard Drive formatted fat32 problems"
date: 2009-07-25
forum: General Help
---

### Post by Pr0_newbie on 2009-07-25
Just installed Ubuntu besides Windows XP.  Completely new to Linux.  I like what I see so far!

I do have a problem getting my USB FAT32 Hard Drive to be recognized.  The drive works in XP just fine.  When I try to boot into Ubuntu with the drive plugged in, the load screen just hangs, I need to reset.  When I boot into Ubuntu THEN plug in the drive, nothing happens.

I've read/googled may posts on this subject and I'm still lost.  Can anyone help???

Here is some info that may help.....

dad@dad-desktop:~$ sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002fd15

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8918    71633803+   7  HPFS/NTFS
/dev/sda2            8919        9964     8401995    5  Extended
/dev/sda5            8919        9913     7992306   83  Linux
/dev/sda6            9914        9964      409626   82  Linux swap / Solaris
dad@dad-desktop:~$ 

------------
dmesg output....

[  116.508021] usb 1-6: new high speed USB device using ehci_hcd and address 2
[  116.718485] usb 1-6: configuration #1 chosen from 1 choice
[  116.775845] Initializing USB Mass Storage driver...
[  116.777370] scsi4 : SCSI emulation for USB Mass Storage devices
[  116.777630] usbcore: registered new interface driver usb-storage
[  116.777634] USB Mass Storage support registered.
[  116.797975] usb-storage: device found at 2
[  116.797978] usb-storage: waiting for device to settle before scanning
[  121.796264] usb-storage: device scan complete
[  123.380018] usb 1-6: reset high speed USB device using ehci_hcd and address 2
[  125.132022] usb 1-6: reset high speed USB device using ehci_hcd and address 2
[  126.884017] usb 1-6: reset high speed USB device using ehci_hcd and address 2
[  128.636018] usb 1-6: reset high speed USB device using ehci_hcd and address 2

----------

lsusb output

dad@dad-desktop:~$ sudo lsusb
Bus 001 Device 002: ID 0402:5621 ALi Corp. USB 2.0 Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


the lsusb and dmesg commands seem to see the USB HD, but fdisk does not!?


Again, any help would be appreciated.  Thanks!

---

### Post by merlinus on 2009-07-25
Look in System/Preferences/Removable Drives and Media to ensure appropriate boxes are ticked.

You might also try plugging it into a different usb port.  And make sure it is not the first hdd in bios boot order.  If it is, that might explain why ubuntu will not load when it is plugged in beforehand.

---

### Post by Pr0_newbie on 2009-07-25
> **merlinus said:**
> Look in System/Preferences/Removable Drives and Media to ensure appropriate boxes are ticked.

You might also try plugging it into a different usb port.  And make sure it is not the first hdd in bios boot order.  If it is, that might explain why ubuntu will not load when it is plugged in beforehand.

I do not have Removable Drives and Media under System/Preferences/ !???

How to I install that Tool? or is it not necessary?

---

### Post by merlinus on 2009-07-25
What version are you running?  It is in the menu in 9.04.

But perhaps it is not necessary.  Did you try my other suggestions?

---

### Post by Pr0_newbie on 2009-07-25
Ubuntu 9.04 I think.  Just downloaded and installed it.  

I did not try the other suggestions because....

when the USB HD is plugged in, upon booting .... it DOES boot to my internal HD and I get the menu to choose Ubuntu or XP


If I choose Ubuntu WITH the HD PLUGGED IN AND ON, it tries to boot to Ubuntu, but the 'meter' gets to about 10 percent and then just hangs.  It will hang forever.  If (when it's hanging)  reach over and unplug the USB HD, it boots instantly into Ubuntu.

Hope that helps....


Thanks

---

### Post by merlinus on 2009-07-26
Did you check the hdd boot order in bios?  

It would seem that ubuntu looks for some startup files on the external hdd when it is plugged in and active, based upon what you wrote, but they are on the internal hdd.  So when you unplug the external it finds what is needed on the internal.

---

### Post by Pr0_newbie on 2009-07-27
Tonight I checked the bios boot order as suggested. It was on boot from removable. I changed to a. cdrom b. hard drive and disabled all the rest.
 
I get the same thing. When booting Ubuntu with the usb fat32 hd plugged in, it just hangs at the graphical loading window at about 10 percent. If I turn off the hd, the booting continues and Ubuntu loads fine.
 
Another note that maybe of some help. If I get Ubuntu fully loaded THEN turn on the external USB Drive, I see a few seconds of COMPUTER HD activity (Internal HD blinks). The USB 2.0 LED on the external HD DOES turn on. I get no indication, nothing on the screen, and I can not see it in the file browser however.
 
Seems like it wants to recognize and mount the external, but dies for some reason.
 
I even booted windows (where it works fine) and 'stopped' the USB HD before shutting down windows (as I seen some posts mention may be necessary step). Ubuntu will still not see it.
 
Hope this new info can be of some help. Thanks again for the effort and your time.

---

### Post by merlinus on 2009-07-28
Can you try a different usb cable from the external to usb port?  Also, does changing the usb port it is plugged into have any effect?

---

### Post by Pr0_newbie on 2009-07-28
> **merlinus said:**
> Can you try a different usb cable from the external to usb port?  Also, does changing the usb port it is plugged into have any effect?

Tried a different USB cable and different ports.  Same results as before.

Acts exactly the same as mentioned.

---

### Post by Pr0_newbie on 2009-07-28
....just a F.Y.I.  I have a 8GB USB Sandisk thumb drive.  I tried plugging that in and it works fine!  There is a ISO image on it for Backtrack 4 (Ubuntu).  

Plugged in, a few seconds later a window opened with the files displayed.  This works but a FAT32 USB HD does not.   Strange.

---

### Post by merlinus on 2009-07-28
I wonder if it would make a difference if you formatted it as ntfs, and then installed ntfs-config.  IIRC you can do this non-destructively from windows.

---

### Post by Pr0_newbie on 2009-07-29
> **merlinus said:**
> I wonder if it would make a difference if you formatted it as ntfs, and then installed ntfs-config. IIRC you can do this non-destructively from windows.
 
I could try that just for the hell of it, but I'd like to keep it FAT32 for compatibility with numerous devices.  
 
I'll try to unload it and try that this weekend.  Will advise.
 
Thanks

---

### Post by Pr0_newbie on 2009-07-31
> **merlinus said:**
> I wonder if it would make a difference if you formatted it as ntfs, and then installed ntfs-config.  IIRC you can do this non-destructively from windows.

Well, I did as suggested.  I converted the FAT32 external USB drive to NTFS.  I did it from within XP as not to loose the data.

It ACTS exactly the same as when it was FAT32.  If I boot Ubuntu with it ON and Plugged in, the boot screen hangs at 10% (shutting the drive off allows booting to continue).  If I turn the drive ON after Ubuntu has booted .. the USB 2.0 light comes on, the computer internal hard drive flashes for a few seconds, the USB HD light flashes for a few seconds, but I get no popup folder and nothing in the file system browser.

I did NOT install NFTS-CONFIG like you mentioned because I'm not sure how.  I will try to read up on it, or take your instructions if I get them.

Thats where I'm at for now!  ;-)

Thanks!

---

### Post by merlinus on 2009-07-31
```
sudo apt-get install ntfs-config
```

Restart, and look for it in Appications/System.  It is a gui where you can specify a mountpoint for ntfs partitions, and boxes that you can tick so they load on startup.

Restart again, and see what happens.

---

### Post by Pr0_newbie on 2009-07-31
Ok, installed NFTS-CONFIG.  Said it was ok.  Rebooted.  Same as before, it hung at the loading screen with the external HD ON.  Turned it off, continued booting.  When booted, I turned it ON.

Found gui NTFS CONFIGURATION TOOL under System/Administration.  Ran it.  It shows me                       nfts-config

           The follwing new partitions were
           detected and can be configured:

Add  |    Device         |   Mount Point
         /dev/sda1          <Click here to set a mount point>

-Select the partition you want to configure
-Add a name for the mount point
-Click apply

                                   <cancel>   <Apply>


I checked the box under 'add'.  I clicked unter the Mount Point heading a got a cursor.  However...........no matter what I typed, the 'Apply' button did NOT become highlighted!
I tried NTFSHD, /NTFSHD, /NTFSHD/, NFTS1, and a few others.  Seems like whatever I type in is not accepted because it will not highlight the 'Apply' button to continue!

LOL.  Crazy.  Maybe I'm just stupid!  LOL.

I'm close.....   help!

---

### Post by merlinus on 2009-07-31
Try this

```
sudo ntfs-config
```

---

### Post by Pr0_newbie on 2009-07-31
> **merlinus said:**
> Try this

```
sudo ntfs-config
```

Same box popped up, still will not let me type anything that will highlight the 'apply' button.   

HOWEVER...  this time, when I clicked 'Cancel' (my only option) it popped up another box with 1 checkbox available "Enable Write Support on NTFS ...".  I clicked it and hit OK.

The box went away.  I went back to NFTS-CONFIG and it will still not let me type anything that will highlight the 'apply' button.

......?

---

### Post by merlinus on 2009-07-31
I will try and run this on my other computer, and get back with you.  My main machine only runs linux.

---

### Post by Pr0_newbie on 2009-07-31
> **merlinus said:**
> I will try and run this on my other computer, and get back with you.  My main machine only runs linux.

Ok, I appreciate the help.  I really like this Ubuntu for the speed and security.  Who would have thought that a simple external USB HD would cause so much crap!  Must be the user!

Thanks again...will await suggestions.

---

### Post by merlinus on 2009-07-31
The ntfs partition came up in the left-hand side (sda1).  I ticked the box next to it, clicked in mountpoint and deleted all the text, typed in sda1, pressed Enter.

It changed to /media/sda1, and then I could click Apply.

---

### Post by Pr0_newbie on 2009-07-31
> **merlinus said:**
> The ntfs partition came up in the left-hand side (sda1).  I ticked the box next to it, clicked in mountpoint and deleted all the text, typed in sda1, pressed Enter.

It changed to /media/sda1, and then I could click Apply.

Ok, did that and it did as you said....... Box popped up with 2 check boxes.  1 for internal NTFS write support, 1 for external NTFS write support.  I check them both, and clicked ok.  It went away.

 I went to file system and I still don't see the drive.  Going to reboot to see if that does anything.

....?

---

### Post by merlinus on 2009-07-31
Before the checkboxes for internal and external support, I got a dialogue box with sda1 listed and a textbox next to that where I could enter a mountpoint.

I used

```
sudo ntfs-config
```

---

### Post by Pr0_newbie on 2009-07-31
> **merlinus said:**
> Before the checkboxes for internal and external support, I got a dialogue box with sda1 listed and a textbox next to that where I could enter a mountpoint.

I used

```
sudo ntfs-config
```

Yes, after you instructed, I did the same...  I got that box and entered sda1 and it changed it to /media/sda1.  I clicked 'apply' (1st time I was able to do that).  THEN the internal/external NTFS box came up.   

Anyhow, just rebooted.  Still hangs at booting.  When booted and turned on .. same thing happens...  I checked my file system browser and I CAN SEE my Win XP partition (NTFS).  Along with the standard Ubuntu file system view I also installed Dolphin.  That doesn't see the external HD either.  Just thought that might mean something.

Still no go....  Can't see it, and it hangs at boot.

---

### Post by merlinus on 2009-07-31
It seems that you have tried everything, and the problem persists.  Obviously it is not mounting properly, and the few times that it does, linux attempts to boot from it rather than the hdd.

Definitely mysterious.... but I have no more ideas at the moment.  If something should come to mind, I will of course post back.

But if you ever decide to reinstall ubuntu, make sure the external hdd is unplugged completely, not just turned off.

One last thing -- check booting order in bios once again to make sure that the hdd is listed before the external.

---

### Post by Pr0_newbie on 2009-07-31
> **merlinus said:**
> It seems that you have tried everything, and the problem persists.  Obviously it is not mounting properly, and the few times that it does, linux attempts to boot from it rather than the hdd.

Definitely mysterious.... but I have no more ideas at the moment.  If something should come to mind, I will of course post back.

But if you ever decide to reinstall ubuntu, make sure the external hdd is unplugged completely, not just turned off.

One last thing -- check booting order in bios once again to make sure that the hdd is listed before the external.

Will do...I want to thank you for the time you spent trying to help out!  I'm getting tired myself and need to put back a few more rum's and hit the sack!  I won't give up!

Just a FYI ..... When I was installing Ubuntu ... I had a HELL of a time!  It keep hanging (external USB 2.0 FAT32 HD connected).  On a hunch, one of the times I tried installled I reached over and shut it OFF.  Ubuntu installed GREAT!

I'm now thinking Ubuntu just don't like my particular external usb drive!

Again, thanks for the help.  I really appreciate it.  You are a credit to these forums!

Cheers!

---

