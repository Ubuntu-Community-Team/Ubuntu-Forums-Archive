---
title: "Mounting a CD"
date: 2010-12-02
forum: General Help
---

### Post by RoflHaxBbq on 2010-12-02
So I decide to replace Windows with Kubuntu a few weeks ago.
I burn a DVD with all the stuff I want to keep, then install Kubuntu.
The install all goes well, and I insert the DVD I burn, and it comes up in Dolphin as "UDF Volume"
I copy the files off this DVD onto the hard drive.
And then I download and install WINE so I can play some of my games.
I insert the Warcraft 3 CD, and nothing.
Nothing comes up in Dolphin, and Kubuntu doesn't even seem to realize that I have inserted a CD.

How can I make this disc come up in Dolphin?
And once I have mounted(Is that what it's called?) the CD, what do I have to type into terminal to launch the setup.exe?
Isn't it something like:

wine dev/cdrom setup.exe

Thanks in advance,
-RoflHaxBbq

---

### Post by RoflHaxBbq on 2010-12-02
Or perhaps I should replace Kubuntu with Ubuntu.

What do you people think?

Will a noob like me be better off with Ubuntu?

---

### Post by kitsune7 on 2010-12-03
Another user posted a good tutorial for using wine with Warcraft 3.
You can find it here: 
[http://ubuntuforums.org/showthread.php?t=45407]("http://ubuntuforums.org/showthread.php?t=45407")

---

### Post by RoflHaxBbq on 2010-12-04
Thanks for the reply, but that isn't the part I'm having trouble with.

That tutorial assumes that the CD is already mounted.

I'm having trouble with the actual mounting of the CD.

-RoflHaxBbq

---

### Post by kitsune7 on 2010-12-04
Does your computer have the ability right now to mount other drives (for example a flash drive)?  And if so have you tried to see if it was a problem with the disk itself (in other words, inserting different CDs/DVDs and seeing if they mount)?

---

### Post by RoflHaxBbq on 2010-12-04
My flash drive automatically mounts.

And it isn't a problem with the disc.

---

### Post by kitsune7 on 2010-12-04
Well if no CDs or DVDs work at all you may want to try mounting it manually with: **sudo mount /media/cdrom0/ -o unhide**

This should mount it and make sure all the files are visible (just in case).

Also you can unmount with: **sudo umount /media/cdrom0/**

---

### Post by RoflHaxBbq on 2010-12-04
I inserted the Warcraft 3 CD, then opened terminal and typed what you said.

It returned an error:

Can't find /media/cdrom0 in/etc/fstab or /etc/mtab

---

### Post by kitsune7 on 2010-12-05
Sorry, I didn't mention it may require more work under certain circumstances.  Here's a link that shows greater detail on how to mount a CD manually when the command I showed doesn't work by itself: [http://www.linuxconfig.org/HowTo_mount_cdrom_in_linux]("http://www.linuxconfig.org/HowTo_mount_cdrom_in_linux")

---

