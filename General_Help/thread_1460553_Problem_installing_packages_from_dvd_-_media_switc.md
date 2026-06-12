---
title: "Problem installing packages from dvd - media switching"
date: 2010-04-22
forum: General Help
---

### Post by wyrdrat on 2010-04-22
I have the Ubuntu 9.10 Karmic Complete 10 DVD set. I installed it to my computer and added all of the DVDs, all the packages show up in Synaptic. However, when I install something that has dependencies on the other disks I am repeatedly asked to change the disk after every file. To rule out any GUI or other software issues, I reinstalled Ubuntu to a command line and added the DVDs with apt-cdrom add and tried to install packages with apt-get install, but get the same problem. So it seems to be an issue with apt.


 I previously had Debian 5 Lenny on 5 DVDs, when I installed packages it would fetch everything off DVD1 and then ask for DVD2 and fetch everything from that and so on. However, with Ubuntu it fetches something off DVD1 and then asks for DVD2 and fetches something off that and then it asks for DVD1 again and so on. Not only is this inefficient and time consuming, but its liable to wear out the DVD drives tray mechanism! I'm sure that it is meant to behave like Lenny did and not do this.


 I have searched the internet, but not found anything about this. I do not have broadband and I'm installing Ubuntu to a couple of old PCs, so using the online repositories is out of the question.


 Thanks for any help.

---

### Post by wyrdrat on 2010-04-23
This is apparently a bug in Apt.

I'm just wondering if I got Apt and all of it dependencies from Lucid, would it fix or break karmic?

---

### Post by wyrdrat on 2010-05-02
Kind of a fix:

Created a directory on the hard disk (you will need about 32GB) called karmicrepository and created subdirectories called main1 - main3, multi1 - multi6, uni1 - uni6 etc. I then copied all the folders from the pool directory of each DVD into the hard drive directories.  I used the command line tool in terminal

 	Code:
 	cp -R /cdrom/pool/main /karmicrepository/main1 
I found that copying and pasting in Dolphin missed some files. I then created a Packages.gz file by typing into terminal, having navigated to the karmicrepository directory

 	Code:
 	apt-ftparchive packages ./ ¦ gzip > Packages.gz 
I then opened /etc/apt/sources.list and typed in:

deb file:/karmicrepository ./

Then in terminal:

 	Code:
 	apt-get update 
Now I can use the repository properly.

I thought it might help anyone who purchased DVDs for Karmic and are unable to use them because of the bug in apt and who do not have an internet connection to the computer they are installing it to. Of course this doesn't help if you don't have a spare 32gb on your hard drive ...

Incidentally, has anyone tried the Lucid DVDs?  Has the apt bug been fixed?

---

