---
title: "How to reinstall MBR?"
date: 2011-07-01
forum: General Help
---

### Post by mrbison on 2011-07-01
Hi, 
I'm pretty much a linux noob, need some help. For some reason after I accidentally put ubuntu (meerkat) into hibernation it won't load OS upon turning back on, shutting the computer down does the same thing. I get this error message: No Boot Device Available, Press Enter to Retry. 
For some reason my OS loads no problem if I am just restarting my system. This just started happening out of the blue. 
I've already reinstalled a couple of times off the live CD and also deleted and reinstalled GRUB2 with no luck. 
Now I'm thinking about trying to delete and reinstall my MBR, but I don't know the safest/best way to do this. Can I do this with gparted? Is this something that can only be done in terminal? I've seen commands like install - mbr ... should I use this route? 

Thanks!

---

### Post by psusi on 2011-07-01
Reinstalling grub2 IS reinstalling your MBR.  Also if it boots fine, then there is nothing wrong with the MBR.  If it won't resume from hibernation, then there's a more subtle problem, likely with your bios.

---

### Post by nmaster on 2011-07-01
installing from the live cd will over write the MBR. i agree that you may have a bios problem.  do you get errors during the install? it could also be a problem with the disk.

---

### Post by mrbison on 2011-07-01
No errors during install... I've even installed different distros (fedora, ubuntu, mint) to check if it was a problem with ubuntu or the a live disc...

If it is a problem with BIOS, how do I check this? Is there a way to "re"-setup my BIOS?

Thanks!

---

### Post by psusi on 2011-07-01
Check with your motherboard manufacturer and see if they have a bios update available.

---

### Post by dabl on 2011-07-01
> **mrbison said:**
> 

Is there a way to "re"-setup my BIOS?



Yes.

Shortly after you power on your computer, you see a message about entering "SETUP" or "BIOS" -- you have to press a F key or a key combination.  Press that key or combo.

Now look at the menu tabs along the top.  Depending on your BIOS OEM and version, there may be a tab labelled "Boot".  One of the menu items on that is "Boot Device Priority".  Open that one and make sure that your optical drive is in first position, and your hard disk drive is in second position.  Possibly there will be another menu item under "Boot" named "Drives" -- you might need to enter that one and make sure that it sees your hard disk drive.

Normally F-10 saves the BIOS settings and lets your reboot, after confirming the save.

---

### Post by varunendra on 2011-07-02
> **mrbison said:**
> I get this error message: No Boot Device Available, Press Enter to Retry. 
For some reason my OS loads no problem if I am just restarting my system.
This also suggests that your BIOS may not be getting enough time to detect the hard disk before it skips to the next boot device. By the time you reboot, the hard disk has been properly initialized and ready to communicate. This may explain why it boots ok after a reboot.

If this happens to be the case, then check your BIOS to see if there is any setting to delay the 'boot-device-detection-time'. If there is, setting it to 5 sec. should be enough.

---

### Post by mrbison on 2011-07-02
So I did know about the BIOS setup upon restart by pushing a F key on restart. I had already checked to make sure that the order of bootable devices was correct. What I didn't notice until just now was that above the order of the devices is another list of the same devices (including the hard disc). When I click on these devices, it tells me what is installed for them. For example, when I click on the CD drive, it tells me the name of my installed drive. What I noticed is that when I click on hard disk, it says "none installed!" There dosen't appear to be any options to install one here either. 
So the order of devices is correct, but there is no installed hard drive listed.

---

### Post by mrbison on 2011-07-02
I just made another discovery. The previous post was done from a "shut down" state of the computer. When I enter BIOS setup during a restart, the Hard Disk IS installed. This makes sense because it boots just fine upon restart. Why wouldn't my hard disk be labeled as installed when it is powered on and off instead of restarted? 

varunendra - I like your idea about the BIOS not having enough time, it makes sense. However, I don't seem to be able to locate any options to change the time allowed. At least in the BIOS settings there aren't any options for this - I'll keep looking. 

Thanks everyone!

---

### Post by dino99 on 2011-07-02
i only answer to the main question, because its the only logic sense i've seen:

sudo dpkg-reconfigure grub-pc

---

### Post by varunendra on 2011-07-02
> **mrbison said:**
> I just made another discovery. The previous post  was done from a "shut down" state of the computer. When I enter BIOS  setup during a restart, the Hard Disk IS installed. This makes sense  because it boots just fine upon restart. Why wouldn't my hard disk be  labeled as installed when it is powered on and off instead of restarted?  

varunendra - I like your idea about the BIOS not having enough time, it  makes sense. However, I don't seem to be able to locate any options to  change the time allowed. At least in the BIOS settings there aren't any  options for this - I'll keep looking. 

Thanks everyone!Well, **IF** that really does happen to be the case, then it further suggests - "its time for you to back up your data".

Is there any setting regarding SMART status of the drive? If there is, make sure it is 'Enabled' now. You may also wish to just pullout - plug-back-in the drive to make sure it is not a problem of loose connection. Hard disk 'Self Test' is another recommendation. The basic idea is to make sure the drive is not failing, and if it seems to be - then backup your data!

---

### Post by mrbison on 2011-07-02
> **varunendra said:**
> "its time for you to back up your data".

Definitely. I have already backed everything up - otherwise I'd really be freaking out. ;)

> **varunendra said:**
> Hard disk 'Self Test' is another recommendation.

The weird thing is that I've run self test and there are no reported problems. When I first saw the "no boot device" error, the first thing I thought was that my hdd was bad... all tests say its fine and healthy... so, I dunno. 

Thanks for the other suggestions. I don't know about the "SMART" option, or the physical connection, but I'm going to check those out now. Thanks as usual.

---

### Post by dabl on 2011-07-02
I think varunendra has identified the problem. I have usually seen the "pre-boot delay" function on the same BIOS page where the IDE and SATA channels are listed.

---

### Post by varunendra on 2011-07-03
> **mrbison said:**
> The weird thing is that I've run self test and there are no reported problems. When I first saw the "no boot device" error, the first thing I thought was that my hdd was bad... all tests say its fine and healthy... so, I dunno. 
It is not very uncommon for hard drives to pass self test and other 'surface-tests' while actually being in a 'failing' state.

The reason, I guess, is that these tests only check the communication with the circuit, and the state of the platters looking for any damaged or bad sector areas, while there may also be mechanical problems which these tests may not be able to detect. But I don't really know in deep what all these tests actually test, so it's just my guess.

> **dabl said:**
> I think varunendra has identified the problem. I have usually seen the "pre-boot delay" function on the same BIOS page where the IDE and SATA channels are listed.
I'm obliged! :D But I'm afraid the only way to find out is to try a healthy hard drive if mrbison doesn't have that option in his BIOS.

---

