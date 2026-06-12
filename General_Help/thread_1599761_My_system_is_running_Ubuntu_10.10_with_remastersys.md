---
title: "My system is running Ubuntu 10.10 with remastersys 2.0.17-1. If important The system"
date: 2010-10-18
forum: General Help
---

### Post by pberggren on 2010-10-18
My system is running Ubuntu 10.10 with remastersys 2.0.17-1. The system uses ubiquity 2.4.8 and ubiquity-frontend 1.248.
A live CD created with remastersys can be booted "live", but when trying to installation it will, during copying of files give an error message: "Installer crashed" in a pop-up window, then exiting. When trying from an older remastersys disk, created under Ubunto 10.04 on the same machine everything works fine. In addition the same problem occur on 2 different machines, so there are no problems with the hardware.

The pop-up window also gives the following "explanation:

--------------------------------------------------------------------------------------------

                     p { margin-bottom: 2.12mm; }  [SIZE=1]"The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment. "[/SIZE]


[SIZE=1]---------------------------------------------------------------------------------------------
[/SIZE]
 
I am thankful in advance for any help with this.

---

### Post by fat_larry on 2010-11-26
I have the exact same error and would love a clue as to why this happens!  I have to exclude the /opt folder for my disk to work (there is about 2GB of software in /opt)

---

### Post by ezsit on 2010-11-26
I've benn using remastersys 2.0.17-1 with Ubuntu 10.10 in DIST mode successfully since Maverick's release without any problem. I do not put anything in /opt and never have an ISO file bigger than 1.0 GB and never a problem reinstalling.

Try sticking to the bare minimum when backing up. The more stuff you put in /opt, the more memory your booted system will take to load and run. Keep it small and simple.

---

### Post by ivarn on 2010-11-26
The problem is, you are using the 10.04 version of remastersys.
As you can see on their site, there's a new version for every ubuntu release, and that's because of the installation method and where files are being placed on the system. If you want to backup 10.10, use the remastersys version for 10.10.
And this is why everything works fine when you try to install 10.04.
But remember the iso limit for dvds (4.3gb)

---

