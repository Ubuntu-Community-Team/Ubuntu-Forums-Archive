---
title: "Virtual Box Not Recognizing External Harddrives"
date: 2010-01-09
forum: General Help
---

### Post by joelandsonja on 2010-01-09
I am at wits end here people ...

I am trying to accomplish the simple task of renaming my harddrives on Ubuntu, but the developers of Ubuntu decided that they didn't want anyone to have the ability of accomplishing such a simple task in an easy way! :-x

Alright, I'll try to sum up my problem here ...

I have been trying to get Gparted to work so I can rename my harddrives, but it doesn't want to work. (What a surprise!) So I decided it might be easier to simply install virtualbox and rename the harddrives through the virtual Windows system. The only problem is that Virtualbox won't recognize the harddrives, so I can't bloody well rename them! (Breath ... Breath ... ) 

I hate to say it, but I am getting fed up with Ubuntu ... but I will endure ... I just need some help to get this to work!

Any suggestions folks?

---

### Post by howefield on 2010-01-09
> **joelandsonja said:**
> I am trying to accomplish the simple task of renaming my harddrives on Ubuntu, but the developers of Ubuntu decided that they didn't want anyone to have the ability of accomplishing such a simple task in an easy way! :-x

My money is on the problem being closer to home. :)

> The only problem is that Virtualbox won't recognize the harddrives,

Are these USB drives ?

And which version of Virtual box are you using ?

---

### Post by gashcr on 2010-01-09
well, first thing to check is if you're using the VB-OSE package from the repos. That one won't work with USB devices. You need the full version from Sun to do that ( 
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) ) there is a repo somewhere... but can't find it now...

Second: be sure to add your user to the VBOXUSR group. 

Third: Once in the VM, plug the Disk thru the VBOX device manager. That should get the job done. 

BTW: If the disc is NOT in VFAT or NTFS chances are it won't read neither on Windows...

---

### Post by joelandsonja on 2010-01-10
I appreciate the help, I'll reinstall the full version and see if that is the problem. 

> My money is on the problem being closer to home. :smile:

I love Ubuntu so far, but having the ability to right click on the drive and click 'Rename' was something Windows thought would be beneficial ten years ago. I realize Ubuntu is a work in progress, (Thanks to those who do it!) but adding this feature would be nice.

---

