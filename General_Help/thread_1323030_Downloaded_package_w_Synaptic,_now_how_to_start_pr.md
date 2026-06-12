---
title: "Downloaded package w/ Synaptic, now how to start program?"
date: 2009-11-11
forum: General Help
---

### Post by Andy H. on 2009-11-11
I've downloaded Astronomical Almanac from the Science section of programs shown in Synaptic Package Manager.  The manager went through its routine, now I'd like to use the program, however there's no icon on the desktop and the program isn't listed under Applications>Science or any other categories under Applications.

I've been following the steps in Keir Thomas' "Pocket Reference Guide," which worked fine for the example cae he provided, but am not able to get this software to run, figure out where the files were downloaded to, or find any kind of start icon for the program.

I've tried this under Ubuntu 9.04 and 9.10 with the same results.

What step am I missing in order to download and use Linux software applications?

Thanks,

  -AH

---

### Post by Andy H. on 2009-11-11
Bump.

---

### Post by oldos2er on 2009-11-11
Type **aa** in a terminal.

---

### Post by Andy H. on 2009-11-11
Dup post, see below

---

### Post by Andy H. on 2009-11-11
Thanks Ann.  I appreciate your burning your 4000th post to give me a hand with this.

I just did that and went through a setup routine for"Ephemeris" but there was no way to "save and exit" and then when I closed the terminal I got a message that a process was running in it, went back through it, and just closed it.

This is the only program I've tried other than "Frozen Bubble" and the .deb program for Skype (both were successful though I have no idea how to get the webcam to work with Ubuntu), that I've tried to install and use since starting my Linux test case on a resurrected laptop.  Is the astronomy program strictly a command line application for professionals to use?  If I'm not just using the wrong program as a download/install test, what do I have to do to get a/the program to set up a startup icon and be able to run?

Thanks,

  -AH

---

### Post by oldos2er on 2009-11-11
aa is CLI only; I don't know much about it beyond that. If you're looking for a GUI astronomy app, there are a few available. Celestia and Stellarium are two of the best ones.

---

### Post by Andy H. on 2009-11-11
Doh!  No wonder there wasn't a screen shot for aa!  :)

It looks like I was trying the wrong program for testing out download and install w/ Synaptic Package Manager.

Thanks,

  -AH

---

### Post by Andy H. on 2009-11-11
I downloaded Stellarium with SPM, am pretty sure its installed as I see it in my Aplications>Science section, and put the launcher on my desktop. However when I try to run it ,either by clicking on the launcher, or by right clicking on the launcher and selecting "open" nothing happens. When I right-click the launcher I see myself listed in the Properties>permissions box, and there don't seem to be any restrictions on my running the program. 

I've found the "readme" and "install" files associated with the program but no other install instructions.  

The Install file states:
> - LINUX USERS :
Look for the binary package matching your distribution.
Which I assume was taken care of by going through the Synaptic Package Manager.

What else do I need to do to get the program to run?

Thanks,

  -AH

---

### Post by Andy H. on 2009-11-11
Bump

---

### Post by oldos2er on 2009-11-11
Usually README and INSTALL files accompany source code. You shouldn't need these if you install the program with Synaptic.

 If you run **stellarium** in a terminal, can you post the output here? It may give a clue as to why it's not running properly.

---

### Post by Andy H. on 2009-11-12
Thanks for the troubleshooting suggestion.  Here's what was returned after attempting to run "stellarium" in terminal mode:

> QProcess: Destroyed while process is still running.
 ------------------------------------------------------- 
[ This is Stellarium 0.10.2 - [http://www.stellarium.org](http://www.stellarium.org) ] 
[ Copyright (C) 2000-2009 Fabien Chereau et al          ] 
 ------------------------------------------------------- 
Writing log file to: "/home/andy/.stellarium/log.txt" 
File search paths: 
  0 .  "/home/andy/.stellarium" 
  1 .  "/usr/share/stellarium" 
Config file is:  "/home/andy/.stellarium/config.ini" 
Segmentation fault
Understanding the case-sensitivity of Linux I also tried running "Stellarium" which returned the following:
> No command 'Stellarium' found, did you mean:
 Command 'stellarium' from package 'stellarium' (universe)
Stellarium: command not foundThe log.txt file and ".stellarium" folder were not found by either browsing my "/home/andy" folder or by a Nautilus search of the entire file system.

A Nautilus search for "stellarium" returned many files and folders with  "stellarium" in their name, however when I try to open the file designated as the 4.7 MB executable file, either by right-click and selecting "open" or by double clicking on it, nothing happens.

I am able to open other text files from Nautilus however not the executable.

Any help would be greatly appreciated.

Thanks,

  -AH

---

### Post by oldos2er on 2009-11-12
Sorry, seg faults are beyond my ability to help.

 .stellarium is a hidden folder; in Nautilus hit Ctrl-H to see hidden files and folders.

---

### Post by Andy H. on 2009-11-12
Thanks Ann.

So this is my first time using Linux.  

Is it often like this when one downloads and tries to install programs?

Thanks,

  -AH

---

### Post by oldos2er on 2009-11-13
> **Andy H. said:**
> So this is my first time using Linux.  

Is it often like this when one downloads and tries to install programs?

 Are you referring to the segmentation fault? No, IMO they rarely happen.

 I googled "ubuntu stellarium segmentation fault", and it appears this is an ongoing problem with stellarium. See [https://bugs.launchpad.net/stellarium/+bug/478117](https://bugs.launchpad.net/stellarium/+bug/478117). Are you using ATI video drivers?

---

