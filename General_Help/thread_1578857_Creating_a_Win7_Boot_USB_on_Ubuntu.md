---
title: "Creating a Win7 Boot USB on Ubuntu?"
date: 2010-09-21
forum: General Help
---

### Post by lostkid on 2010-09-21
I've spent the past several hours trying to determine how I can mount a Windows 7 ISO onto my USB drive using Ubuntu.  I have followed [this](http://ubuntuforums.org/showpost.php?p=9458199&postcount=6) post, as it is the only thing that came up on Google after hours of searching (mostly it shows how to make a Ubuntu USB drive on Windows, not vice versa.)

Using the method in that post, it seems like I was successful. However, after a few seconds it gave me an error like this.

```

**Load Driver**
A required CD/DVD drive device driver is missing. If you have a floppy disk, CD, DVD, or USB flash drive, please insert it now.

Note: If the Windows installation media is in the CD/DVD dive, you can safely remove it for this step.

```

I can't locate this driver anywhere, and have never had a similar problem. I don't quite know what to do, so any insight would be helpful.

---

### Post by lostkid on 2010-09-21
Help! Quick! :( Within 5 minutes, my thread is buried and I'll never get support...

---

### Post by Elfy on 2010-09-21
No - what happens is people get fed up with people bumping too soon, please leave 24 hours before bumping your threads. It also stops people who search for unanswered posts from finding it.

---

### Post by lostkid on 2010-09-21
True enough, I apologize.

I'm very frustrated at the moment, though that's no justification. I appreciate any help that people have to offer and won't bump so hastily. ;P

---

### Post by wilee-nilee on 2010-09-21
Does the thumb have a boot flag on it? Look in gparted, right click on unmounted thumb, manage flags, click flag.

Otherwise just go to a Windows computer you have admin access on download the ms thumb loader for W7. It has to be a legit iso to work though. Not saying yours isn't, just stating the situation.

---

### Post by lostkid on 2010-09-21
Yes, I formatted the thumb as a NTFS system and it automatically added a 'boot' flag. My Windows ISO is genuine, however I don't have access to a computer running Windows as this is my only computer and it only has Ubuntu on it. I have tried running the thumb loader for W7 through Wine, yet it simply says "Starting ... " in the taskbar and then that disappears and nothing else occurs.

---

### Post by wilee-nilee on 2010-09-21
> **lostkid said:**
> Yes, I formatted the thumb as a NTFS system and it automatically added a 'boot' flag. My Windows ISO is genuine, however I don't have access to a computer running Windows as this is my only computer and it only has Ubuntu on it. I have tried running the thumb loader for W7 through Wine, yet it simply says "Starting ... " in the taskbar and then that disappears and nothing else occurs.

Some have succeeded at this method, some don't. You could actually install that iso to virtualbox then use it to load your thumb. You just need the puel version off the web, and to add your name to the user-group-virtualbox, then add the thumb to he usb in setting with the W7 install off. So you can just transfer the iso to the virtual via the thumb then load it correctly and have a goos ol time in the town tonight. You will need a least a gig of ram in the computer 2 is even better.

You could also just activate it in the virtual if thats your ultimate goal, depending on what you need it for.

I have a ISO of W7 as well it was a student upgrade download, I have the .exe version well and 2 dvd's. Never use it though I like open source the best. Except right now when I'm defragging a external shared in ntfs.

---

### Post by lostkid on 2010-09-21
> **wilee-nilee said:**
> Some have succeeded at this method, some don't. You could actually install that iso to virtualbox then use it to load your thumb. You just need the puel version off the web, and to add your name to the user-group-virtualbox, then add the thumb to he usb in setting with the W7 install off. So you can just transfer the iso to the virtual via the thumb then load it correctly and have a goos ol time in the town tonight. You will need a least a gig of ram in the computer 2 is even better.

You could also just activate it in the virtual if thats your ultimate goal, depending on what you need it for.

And this brings up the reason why I am trying to regress to Windows. This is foreign to me. I can say however, that my computer has 4GB of ram, so it should indeed be capable of running this. I do not know what virtualbox is, I do not know what the "puel" version is, I do not know where the user-group-virtualbox is, etc.

This is why nothing ever works for me. :KS

---

### Post by wilee-nilee on 2010-09-21
> **lostkid said:**
> And this brings up the reason why I am trying to regress to Windows. This is foreign to me. I can say however, that my computer has 4GB of ram, so it should indeed be capable of running this. I do not know what virtualbox is, I do not know what the "puel" version is, I do not know where the user-group-virtualbox is, etc.

This is why nothing ever works for me. :KS

[http://www.virtualbox.org/](http://www.virtualbox.org/)

I suspect if I walked you through my description, that you might recognize at least a use for open source. Once you know just the basics, and your not afraid of a little terminal time, on occasion; you will be the master of windows at the least. Good luck;)

---

### Post by lostkid on 2010-09-27
> **wilee-nilee said:**
> Some have succeeded at this method, some don't. You could actually install that iso to virtualbox then use it to load your thumb. You just need the puel version off the web, and to add your name to the user-group-virtualbox, then add the thumb to he usb in setting with the W7 install off. So you can just transfer the iso to the virtual via the thumb then load it correctly and have a goos ol time in the town tonight. You will need a least a gig of ram in the computer 2 is even better.

You could also just activate it in the virtual if thats your ultimate goal, depending on what you need it for.

I have a ISO of W7 as well it was a student upgrade download, I have the .exe version well and 2 dvd's. Never use it though I like open source the best. Except right now when I'm defragging a external shared in ntfs.

Finally getting to trying this... will post if it works.

---

