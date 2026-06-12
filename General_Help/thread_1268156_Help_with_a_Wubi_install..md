---
title: "Help with a Wubi install."
date: 2009-09-16
forum: General Help
---

### Post by Lord-Koga on 2009-09-16
Hello all, this is my first post on the forums and I did not know where else to put the thread: so I apologize if I have misplaced it. I was wondering if anyone knew of a way to access file from Windows inside a Ubuntu 9.04 install made using Wubi. It is not an absolute must but would be nice to access files from one to other rather then storing them on both. I am not a total novice nor am I unduly afraid of complex solutions.  Thank for the the help and time!

EDIT: Sorry if this has been posted before, I should searched the forums first. (At least I admitted to not doing so :) ) So  sorry to the people on here who may have answered this question many times before.

---

### Post by itsjareds on 2009-09-16
No problem.

And hey, post here if you need help with a HowTo.

---

### Post by Lord-Koga on 2009-09-16
So Jared would you happen to know how to access windows files (mostly media files) from Ubuntu?

---

### Post by Hogosha on 2009-09-16
the absolute easiest thing to do would be to make another partition just for files you want to share.

I have a 20 GB partition that the Windows My Documents folders are in and i have it automounting in ubuntu.

---

### Post by Lord-Koga on 2009-09-16
Making a new partition would be an option but I have very limited space. And I am not in a position to buy an external drive. The main reason I wanted to have access was so I would not need to use extra space. My idea was that I would have access to all my files on the disk: regardless what OS I'm using. If that's possible it would be great.

---

### Post by itsjareds on 2009-09-16
Which version of Windows are you using, and what type filesystem are you using on Ubuntu (EXT3 by default, unless you changed it)?

I installed Ext2FSD, an EXT filesystem driver for Windows XP, on Windows. It lets you read your Ubuntu partition like any other drive in Windows Explorer. The driver works without any hiccups on XP and Vista, though I can assure you it's buggy on Windows 7 RC as it gives me BSoDs often when I try to access the Ubuntu partition.

[Read the HowTo on this forum post.]("http://ubuntuforums.org/showthread.php?t=436923")

---

### Post by Lord-Koga on 2009-09-16
Using Windows XP, and using ext3 file system. I was more hoping to get to windows files in Ubuntu not vice versa.

---

### Post by itsjareds on 2009-09-16
Wow, I completely misread then. :D Try viewing the host directory (/host). This should contain your Windows partition.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?")

---

### Post by Lord-Koga on 2009-09-16
Problem Solved THANK YOU JARED!!!

---

