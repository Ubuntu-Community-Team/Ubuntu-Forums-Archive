---
title: "URGENT: Klam AV"
date: 2009-11-16
forum: General Help
---

### Post by aznsmartj0ck on 2009-11-16
Please help me!  My Ubuntu system has totally crashed, and I am in dire need of help!

So I just ran a Klam AV scan throughout my whole Ubuntu system, and it found about 15 "problems".  So I click quarantine all, assuming nothing bad will happen.  Unfortunately, the computer immediately started glitching.  After much struggle, I got it to reboot through the terminal, and when it turned on again, the desktop refuses to load!  So I reboot into recovery mode, and completely remove Klam AV and all its plugins with a sudo-apt get remove and sudo apt-get autoremove.  I thought this would restore the quarantined files.  However, the system is STILL refusing to start up correctly.  The network is not working correctly now, so I cannot reinstall KlamAV.  Does anyone have any idea how I can possibly restore Ubuntu's core system files without having to reinstall the whole system?  Thanks a billion....

---

### Post by JBAlaska on 2009-11-16
Haven't used Clam on Linux, but if it works like "other" AV's with quarantine, you should be able to restore the quarantined files to their original locations..

But..Since you completely removed Clam, I'm not sure if you lost your quarantine directory as well.

Hopefully someone else can answer that for you, and tell you where Clam keeps the quarantined files.

---

### Post by MonoDeem on 2009-11-16
Can you please show us the output of the following command ?

```
ls -l ~/.klamav/quarantine
```

---

### Post by phillw on 2009-11-16
I'm still trying to get my head round CLAM-AV removing linux files - Are you sure you aren't using WUBI or another emulator to run Ubuntu under windows ?

Phill.

---

### Post by aznsmartj0ck on 2009-11-16
There is nothing in the quarantine folder.  any sugguestions?  any help would be appreciated.

---

### Post by aznsmartj0ck on 2009-11-16
There is nothing int he folder
any ideas?

---

### Post by Jazzy_Jeff on 2009-11-16
The only thing I can suggest is to make sure everything is backed up and do a clean install. This will probably be the fastest way to fix your system. I don't think many people have experience with the AV programs. Good luck.

---

### Post by MonoDeem on 2009-11-16
> **aznsmartj0ck said:**
> There is nothing in the quarantine folder.  any sugguestions?  any help would be appreciated.

It's empty or simply doesn't exist ?

---

### Post by Lucky75 on 2009-11-16
You could try just installing gdm/kdm again and see if that gets you anywhere.

---

### Post by phillw on 2009-11-16
> **jazzy_jeff said:**
> the only thing i can suggest is to make sure everything is backed up and do a clean install. This will probably be the fastest way to fix your system. I don't think many people have experience with the av programs. Good luck.

+1

---

### Post by aznsmartj0ck on 2009-11-16
Thanks for your help.  Do you have any idea I can back up my files? considering that I can't even start Ubuntu atm...

---

### Post by aznsmartj0ck on 2009-11-16
It's empty

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
Boot the live CD and then copy the files to a drive or folder that won't be affected by reformat of install drive.

---

### Post by MiCK.ca on 2009-11-16
I have heard in the SUSI linux world and perhaps it holds true in Debian based OS as well, but Clam can mistake orphan files as threats. because having 15 problems on a linux box sounds more like orphans not "malware". 

not to sound naive but there really hasn't been any threats on a desktop level.

---

### Post by phillw on 2009-11-16
> **aznsmartj0ck said:**
> There is nothing int he folder
any ideas?


W00T ??? Klam AV's own site shows the last ubuntu version as being for ubuntu 6.10 ?

There forum shows  > (cur) (last)  [14:18, 17 November 2007]("http://klamav.sourceforge.net/klamavwiki/index.php?title=Talk:FAQ&oldid=1554")You really used KlamAV ?

Phill.

---

### Post by aznsmartj0ck on 2009-11-16
I just tried that.

Unfortunately, many of the files are denied access...I was an administrator on my Ubuntu installation, and now I can't access my own files from the live cd...any help?

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
In the live CD ```
sudo nautilus
``` to get a root nautilus window. You should be able to move them then. Or you can ```
sudo cp /yourfiles /backupdrive
``` in the terminal. Either way will get her done.

For your enlightenment antivirus software are really not needed on Ubuntu. Or any other Linux distro. At least that I know of.

---

