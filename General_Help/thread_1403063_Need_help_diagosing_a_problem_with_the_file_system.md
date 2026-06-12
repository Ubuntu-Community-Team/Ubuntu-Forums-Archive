---
title: "Need help diagosing a problem with the file system"
date: 2010-02-09
forum: General Help
---

### Post by Corporate Boy on 2010-02-09
I am in the process of learning how to navigate Ubuntu, so I'll admit I am a complete noob.  I have encounter a problem I need help resolving.  Thanks in advance!

Environment - I have installed Ubuntu 9.10 onto a Dell Inspiron laptop.  I then installed the Ubunutu Studio kernal on top of the original installation.   This has worked for me for a couple of month and has served as a playground for experiments.


Problem - All personal files and settings are lost!  This was after several months of quality use.  I booted up the machine  and noticed that my desktop background was gone and the panel menu system was gone.  Only one panel was on the desktop and it contained only one drop down menu, clock, network connection and battery life.  It was located in an unusual place at the top of my desktop.    This was completely different from the default install settings I was using before.  I then noticed that all contents in the folders under my user folder were gone.  The contents in the user folder were still there, which was only 1 file, an image that I had used as the desktop background. However, it was not the background now.  I didn't have many personal files saved on this machine.  Everything was backed up besides this C++ program that was done in Eclipse and located in the workspace folder under my user folder.


What I am hoping to do -  I hope that I can recover the files that were lost.  I was using Eclipse and had a C++ model that I didn't have backed-up.  I also want to find out what caused the problem so that I can avoid it in the future.


Before I noticed the problem I was having problems with what I think was my Flash plug-in for Firefox.  I looked up on the web how to uninstall my back version of Flash and re-install the latest version.  I had problems viewing flash sites and youtube.  Once I got the latest version installed, my flash problems went away.  During this time I was experimenting with the package manager and the add/remove program tool to find a plug-in that would work and removed what I thought was unnecessary multimedia applications.  I ended up using a command line copy from a help forum to uninstall flash, grab the latest and install it.

Nothing I did I thought would cause my files to disappear, but then again I am noob.  Any suggestions on what caused this?  Or what logs might be useful to find out the root of the problem?

I am hoping that the files still exist, but someone the file system that gnome is running on has it hidden.  Is this even possible?   

If I am completely hosed, I'll probably just format and re-install Studio, but I would love to know what I did wrong.  Right now I am having problems finding anything useful in the logs.

Thanks for your help.  I am still excited about Ubuntu and hope to become fluent in it.

---

### Post by Corporate Boy on 2010-02-09
I just ran executed the Update manager and received the following error message -

> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


Other weirdness I am experiencing is that all files under the desktop folder are there.  They contain older dates.

I also the Stellarium menu system is hosed up.  The graphics are all weird when I try to use the menu.

Also all my Battle For Wesnorth saved games are gone. 

Normally I would just format and reinstall, but I would love to get these C++ programs back.

---

### Post by mdurham on 2010-02-09
You must stop running that system NOW, the more you run it, the more damage you are doing. Boot from a live CD and take a look from there. Maybe you will find the missing C++ things.

---

### Post by Corporate Boy on 2010-02-09
Thanks.  I'll boot from a CD and see what happens.  What type of damage is being done?  Do know what would have caused this state?  

Thanks

---

### Post by Corporate Boy on 2010-02-10
Finally got a break from shoveling snow to mess around with this problem.  I rebooted from the CD, but unfortunately I don't see any of my old files.

Apparently I was screwed up the public key at some point, which prevent the update manager from working properly.  I have a feeling what I did to cause that problem is related to this problem.  I also started this thread which helped my resolve the public key issue.  I am not really sure what the public key does.  I need to go to school with Ubuntu, rather then just press buttons.

[http://ubuntuforums.org/showthread.php?t=1403063](http://ubuntuforums.org/showthread.php?t=1403063)

Do you think it is still possible to recover my files or is it a lost cause?  If it is a lost cause, I would love to know what I did wrong to avoid in the future, but I assume just format and reinstall and start rebuilding this C++ project from scratch.

Anyway... thanks!

---

### Post by mdurham on 2010-02-11
> **Corporate Boy said:**
> I would love to know what I did wrong to avoid in the future, but I assume just format and reinstall and start rebuilding this C++ project from scratch.

Anyway... thanks!
What you did wrong was to not backup your data.

There is a program in the repos called "Testdisk" that among other things helps recover data from corrupt drives.

---

