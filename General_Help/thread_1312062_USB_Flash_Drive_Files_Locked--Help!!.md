---
title: "USB Flash Drive Files Locked--Help!!"
date: 2009-11-02
forum: General Help
---

### Post by SVEN1 on 2009-11-02
Got a bit careless the other day transfering stuff from my desktop to my wife's computer. Instead of unmounting the Flash drive before pulling it out of my computer, just pulled it out. Well all files are padlocked, tried all sorts of ways to change permissions to the individual files and the drive itself. It will not allow me to.

The computer store said to reformat it. How do I do that with Ubuntu 8.10?? I am not worried about deleting files on it.

The drive is a Centrios 4GB-200x #2518663

Thanks

---

### Post by Bradj47 on 2009-11-02
The following process WILL clear your flash drive of all your files. 

Conveniently, I was just looking up how to do this. This worked for me:

Start up gparted. Don't have it? Then: 
```

$ sudo apt-get install gparted

```
*Wait for it to download and install*
Now run it:
```

$ sudo gparted
======================
libparted : 1.8.8
======================

```

A window should pop up. GParted -> Devices -> wherever your flash drive is. Chances are it's probably *not* /dev/sda. Make sure you know what drive you are selecting. If you do this to your main hard drive (which is probably /dev/sda), your operating system, all your files, are gone forever. A trick is to try clicking on different the different drives listed and see which one is ~4 GB. For me, it was /dev/sdc because /dev/sda is my main hd, /dev/sdb is my second hd loaded with Solaris, and /dev/sdc is the only flash drive plugged into my computer. If you have multiple flash drives plugged in, it would probably help to eject and remove them. 

Ok, I'm done giving you tips on making sure what drive is the one you're looking for. Now the dangerous part. Select everything in the frame listing the partitions of the drives. If there's only one thing there, good. That's slightly less work to do. Click the 'New' button and fill out the fields to match the screenshot I attached. Make the file system fat32 if you want Windows computers to be able to run it. And change the label to whatever you want to call your flash drive. For the new size (MiB) field, make it as big of a number as it will let you. Click 'Add'. Then, back in the main GParted window, something should have happened at the bottom of the window. Like something moves up. You'll know what I mean. Click the 'Apply' button at the top of the window. Once you do that, everything on your flash drive is being cleared off. 

When it's done, quit out of GParted and pull your flash drive out of your computer. Plug it back in again and it should open either a blank file browser window, or a dialog asking what you want to do with the device. Your flash drive is now clean and you should be able to put stuff on it again.

---

### Post by SVEN1 on 2009-11-03
Thanks will try it

---

### Post by SVEN1 on 2009-11-03
Went thru all the steps. A box came up that said an error occured. Now the USB drive when plugged in will not even open, no icon appears on the desktop.  
Suggestions?
thanks

---

### Post by Bradj47 on 2009-11-03
Even though it doesn't show up on the desktop, it's probably still mounted (with the experience I've had). Try opening up GParted again and see if it's in the devices menu as /dev/sdx, and repeat the process again. Or if that doesn't work, try plugging it into a Windows computer and see if it shows up. Then format it there.

---

### Post by SVEN1 on 2009-11-03
It's good to go now.

I just took it over to the laptop with windows and reformatted the USB drive. Took back over to my Ubuntu desktop, inserted it into my USB port and it now mounts and icon appears on the desktop.

Thank you very much
Have  a great week:popcorn:

---

### Post by Bradj47 on 2009-11-03
No problem. 
Have a great *month* ;)

---

