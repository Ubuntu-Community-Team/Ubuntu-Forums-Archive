---
title: "hfs+ and backup"
date: 2009-07-17
forum: General Help
---

### Post by greenuser101 on 2009-07-17
How do I access the hfs+ partition on my Mac? I installed everything to do with hfs (hfsprogs etc.) but I still cannot access my folders on my Mac partition, I get an error like "no permission to access these files" and no opportunity to authenticate. Also the files are labeled as "unreadable". Also I'd like to know how to use sbackup (or another backup system) to make a complete clone of my ubuntu partition, at least complete enough to restore the system from it, if booting from an external disk is too much to ask.

---

### Post by greenuser101 on 2009-07-18
I found a partial answer to my question, and as I already know how hard it is to find anything here, I give it; maybe it will help somebody. There is this tool called Clonezilla ([http://gpartedclonz.tuxfamily.org/index.php](http://gpartedclonz.tuxfamily.org/index.php)) which claims to be able to clone a partition. Haven't tried it, so I cannot recommend it, but I see my thread gets visitors so somebody might be interested. Seems it's worth my while to stay on board, at least as an observer - hope that won't offend anybody.

---

### Post by 3rdalbum on 2009-07-18
I found that I could only access my HFS and HFS+ volumes from the command-line programs (hmount, hls, hcopy etc) and I think I had to be root in order to do it.

Clonezilla can read HFS partitions so you're alright there.

---

### Post by greenuser101 on 2009-07-18
I just found something - MacFUSE ([http://code.google.com/p/macfuse/](http://code.google.com/p/macfuse/)). Does somebody know about this? It seems to be a dicey thing yet, but some people seem to get results.

---

### Post by greenuser101 on 2009-07-18
Thank you, 3rdalbum, for your tip. Can you tell me what version of ubuntu you are using, and what version of Mac OS? I still have install discs of Tiger; if that works better I could reinstall it.

---

### Post by skullmunky on 2009-07-18
If you are able to open the HFS+ volume, but you just can't get into any of your folders (it says permission denied when you try), then it may be because the filesystem is being read correctly, and Linux is respecting the file permissions that were set in OSX.  I have a Mac laptop and had this problem with reading files in my (OSX) home directory when I'm booted into Ubuntu.  Both OSX and Linux are UNIX operating systems, and so they share some underlying features for controlling users and access to files.  

Both control access using the "User ID", a number for each user on the system.  The problem is that in Ubuntu you'll probably have a different ID than you had in OSX.  On my laptop, there's just one user - OSX uses "501" for the first user ID number, but Ubuntu uses 1000.

There are probably some uber sneaky ways to fix this but the way I did it was to log into OSX and just set the permissions on my user folder there so it's world-readable.  Yeah, that's sort of a security flaw, but since it's not a shared machine and I don't run any servers off it I took the chance.

You can also get at your files from the command line using sudo, because it gets around the permission issue.  You could also create a user (in Ubuntu) and specify the same user ID that the HFS+ volume's user had.  

And, lastly, clonezilla should do the trick for you anyway, if you really just want an identical backup of the HFS+ drive onto another HFS+ drive, rather than access to individual files from Ubuntu anyway.  Good luck!

---

### Post by 3rdalbum on 2009-07-18
MacFUSE is a piece of Linux infrastructure that has been ported to the Mac - it's not relevent in this case, but I'll give you 10 points for doing a Google search :-)

I don't think I've tried HFS volumes since Ubuntu 8.04 or maybe 8.10. A couple of years ago (2006) I wrote a GUI wrapper around those utilities but I don't believe it runs anymore (and it was badly-written to rely on certain programs being setuid, I don't want to distribute it anymore in case it causes problems). I don't still have a Mac but when I did it was running Mac OS 9.

Neither of that should matter - the command-line utilities should work regardless of Ubuntu version and regardless of what Mac OS version was used to create the HFS/HFS+ volume.

---

### Post by greenuser102 on 2009-07-20
I registered afresh as "greenuser102" (former "greenuser101") because I am having massive login problems. I am using the opera browser now, as Firefox keeps crashing. How can I uninstall Firefox so it stays uninstalled? I tried sudo apt-get remove firefox and got confirmation, but it's still there. ADMINS: PLEASE DEACTIVATE GREENUSER101 AS I SEEM TO BE UNABLE TO USE IT ANYMORE. Please understand that I don't wish to annoy anybody, I have real trouble that I do not understand and should not have.
Also, for the first time I cannot install the Medibuntu package (which is legal in my country), using a procedure that worked before. (Installed libdvdcss2 though and got DVD playback, so I am fine here but I still want to know what's going on). Can it have to do with the grub-EFI I installed? I installed 64bit Jaunty ubuntustudio on an iMac 7.1. Booting (including restart) works fine w/o rEFIt, but I still get the grub boot menu. And how do I install the flash plugin (64bit) for Opera (which I need to access aon webmail)? I tried it from the popup menu that appeared but it did not work. I know this is not the right place for this post, but I am glad I got in at all, so I hope somebody will read this.

---

