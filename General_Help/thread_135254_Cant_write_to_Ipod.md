---
title: "Cant write to Ipod"
date: 2006-02-23
forum: General Help
---

### Post by WillFerrellLuva on 2006-02-23
I cant seem to be able to put my music files onto my ipod.

When I try to use gtkpod I get an error message that says that the Ipod is a read only file system.

When I try to open amarok or rythmbox with my Ipod mounted they try to open, but they never do.  I guess they just crash right away.  

Ive tried looking on other threads, and tried running gtkpod from the terminal with sudo, but that didnt work either.

Please help me :(

---

### Post by uberlaff on 2006-02-23
Well I had a similiar problem.  I have a nano and after updating the firmware I couldn't write files anymore.  I had to go into GTKPod under the File menu and select Create iPod's Directories, even though they already existed.  I'm pretty sure that this didn't delete any of my music, calendars, or anything.  

This fixed mine.  Let me know if this helps you out.

---

### Post by WillFerrellLuva on 2006-02-23
No, that didnt do it.

When I try that it tells me there was a problem creating the directory.

---

### Post by uberlaff on 2006-02-23
hmm... don't know.  sorry I couldn't help. Anyone else have something?

What generation ipod are you using?

---

### Post by WillFerrellLuva on 2006-02-23
Its a 3rd Genreation, and I have it connected via firewire

Maybe this is related...I also have trouble mounting it at times.  Sometimes its pluged in and the computer doesnt mount it automatically.  When I go to System->Adminstration->Disks it doesnt show up there either

---

### Post by uberlaff on 2006-02-24
I bet that has something to do with it.  Are you sure that the firewire ports are working?  That might be where the problem is.  Do you have anything else to plug in there to test the port?

---

### Post by WillFerrellLuva on 2006-02-25
I connected my ipod to my computer with a usb cable and that seems to have fixed the problem of having amarok and rythmbox crash when I start them with the ipod mounted.

Also havent had a problem mounting the ipod now....yet anyway.

But when I try to write files to the ipod i get the same error about a problem creating the directories, and about it being a read only filesystem.

---

### Post by uberlaff on 2006-02-27
Sweet... at least we have 2 of the problems fixed now.  Have you tried going into GTKPod and under the File menu and select Create iPod's Directories when the ipod is connected via USB?  give this a shot using regular user rights and with the sudo command.

---

### Post by opioid on 2006-02-27
WillFerrellLuva:
[B]
I am having the exact same problem. [/B] I'm trying to use an iPod nano 1GB on Linux. I would guess that yours is also a 1GB, is that true?

See if this error output looks familiar, it's my thread @Gentoo forums:
[http://forums.gentoo.org/viewtopic-t-433660-highlight-.html](http://forums.gentoo.org/viewtopic-t-433660-highlight-.html)

Peace
O

---

### Post by WillFerrellLuva on 2006-02-27
I think there was a problem with the iPod itself.  I used the restore program in windows to reset it and flash the firmware, and after i did that everything seems to be working perfectly.  I was able to write my songs to it from gtkpod without using sudo (before i restored it though I was still unable to create the directories using gtkpod even when using sudo).

As to opioid: I have a 20gb iPod version 3.1, and I never received an error message like that.  Just some ones telling me that there were problems creating directories on the iPod, and another one telling me that it was a read only filesystem.

Thanks for the help everyone

---

### Post by opioid on 2006-02-27
Cool. Would you mind posting your /etc/fstab line for the iPod mount? Thanks a lot.

-O

---

### Post by opioid on 2006-02-27
Cool. Would you mind posting your /etc/fstab? 

Thanks,
-O

---

### Post by Edward The Bonobo on 2006-03-01
A common cause of this problem is...

...have you already got an iTunes database loaded from Windows/iTunes?  If not, borrow a machine and load at least one song.

---

### Post by opioid on 2006-03-01
EtB:

Thanks... I emailed the creator of gnupod.pl and he diagnosed the problem as a bad cable. It's working pretty well now. I think dust in the usb ports was somehow affecting the transfer. I cleaned my case up and tried the usb direct mobo and it started working... before that I did what you suggested and used the restore + iTunes utilities to reformat/rename the ipod. 

Gnupod is **definitely** the way to go if you want to be sure everything's working. Also switching to the dir where the files are works better than adding by specifying a long absolute path (for some reason).

Also, adding one at a time ensures that the tunesdb.xml is written after each song, rather than after many songs... 

If you run into problems, unmount, remount and run ```
gnupod_check.pl --fixit
```. 

And here's the fstab I ended up using, btw (with udev):
```

/dev/ipod  /mnt/ipod  vfat  sync,nodev,nosuid,user,rw,noauto 0 0
none            /proc/bus/usb     usbdevfs        defaults   0   0
```

Thanks,
./O

---

