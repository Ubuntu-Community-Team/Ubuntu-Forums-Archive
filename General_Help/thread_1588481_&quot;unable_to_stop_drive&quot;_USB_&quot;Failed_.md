---
title: "&quot;unable to stop drive&quot; USB &quot;Failed to eject media&quot;"
date: 2010-10-05
forum: General Help
---

### Post by beesblaas on 2010-10-05
I'm using Ubuntu 10.04 LTS
I have a 16Gb USB memory stick (thumb drive) and when I right-click and do "Safely remove drive", I get the following response:
"[B]Unable to stop drive  
Failed to eject media; one or more volumes on the media are busy[/B]"

I can access this drive and the files inside without a problem, it is only when I try to remove it.
This USB drive works fine on Windows XP, and I have checked (scanned it) it on XP,
there are no problems.
Other USB drives work fine on my PC.
There are no other programs open at the time I am doing this.
It does it every time, not intermittently.
What is strange is the icon of the drive shows it's name as: **[COLOR=DarkRed]n "";}[/COLOR]**
in stead of Cruzer or some other readable name.

When I use the disk utility, I get the following:
**Error unmounting: umount exited with exit code 1: umount: /media/n "";: not found**
I cannot do "Check Filesystem" on Ubuntu disk utility:
"[B]Error checking filesystem on volume
an error occurred while performing an operation on "[COLOR=DarkRed]n "";}[/COLOR]" (partition 1 of Sandisk Cruzer): The device is busy[/B]"


NOTE:
This problem resolved itself: After continued use of the USB drive, (using it between a linux and 2 windows computers) it stopped giving me
this message. It could be that a windows 7 system prompted me to fix errors, I cannot remember.
There is still one issue though: When I plug the USB drive into UBUNTU, the name of the USB device is shown as "in the ove" in stead of
"Cruzer" or such. It seems the system grabbed this name from a text file somewhere at some stage.
I do not know how to change it but it does not matter.

---

