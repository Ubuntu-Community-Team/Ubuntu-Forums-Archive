---
title: "What is using up all my harddrive space??!"
date: 2010-09-17
forum: General Help
---

### Post by Wangsta on 2010-09-17
So I STTUUUPPPIDDDLY tried to back up my Ubuntu system in the wrong way...

I have a dual-booted Windows-Ubuntu system with a shared media partition (which is way bigger than my Ubuntu partition). When I tried backing up just my Ubuntu section, I forgot to omit the shared partition. 

So it attempted to copy a compressed version of both my Ubuntu partition AND my shared partition. Ubuntu notified me I had 1.5 Gigabytes left and I realized what was wrong and killed the backup. In an effort to free up some harddrive space, I deleted the half-made backup file. However, even after deleting it, it says I have used up 30.4 GiB of 33.6 GiB... 

I tried using Disk Usage Analyzer, but it doesn't seem to yield any results.
What do I do?! How do I fix this?? [-o<

---

### Post by Wangsta on 2010-09-17
Also, I deleted the file using "sudo nautilus" then just selecting and hitting delete. I'm not sure if that permanently deleted it or not...

---

### Post by linux_tech on 2010-09-18
If you enter these cmds in a terminal they will help keep the system clean.
Clean and autoclean will clear out the local repository of retrieved
package files. Autoremove removes packages that were installed by other packages and are no longer needed . gtkorphan will allow you to remove orphaned packages .

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get install gtkorphan

---

### Post by Randymanme on 2010-09-18
May I ask what app you backed your system up with?  If it was Remastersys, check for a Remastersys folder in /home.

To find it, I have to go to Places>home folder.  After clicking on home folder, I click the "<" to the left of my username. Then a "home' button will appear to the left of my username.  I Click the "home" button and the home folder icon will appear along with the Remastersys folder.  If you used Remastersys, that's probably the elusive culprit.

---

### Post by tgm4883 on 2010-09-18
most likely it's sitting in the recycle bin. Since you deleted it via "sudo nautilus" (btw, you should use gksudo nautilus instead of sudo for graphical applications) it's likely sitting in the trash for root. look for a hidden .Trash folder

---

### Post by Wangsta on 2010-09-18
I used "$ sudo tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /"

I also tried using "gksudo nautilus" and going to the "/root" directory and looked for hidden files. There wasn't any .Trash though...

Where would the root's recycle bin be??

EDIT:  Hold on, in "/root/.local/share/Trash"  there are two folders, "files" and "info."
in "files" is a copy of the "backup.tgz" (hoooorah!) and in "info" is a file called "backup.tgz.trashinfo." I'm going to LEARN from my mistakes this time!!

How should I go about removing these files? Should I just "gksudo nautilus" to this location and delete them myself? Or is there a better way to go about this

---

### Post by tgm4883 on 2010-09-18
> **Wangsta said:**
> I used "$ sudo tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /"

I also tried using "gksudo nautilus" and going to the "/root" directory and looked for hidden files. There wasn't any .Trash though...

Where would the root's recycle bin be??

EDIT:  Hold on, in "/root/.local/share/Trash"  there are two folders, "files" and "info."
in "files" is a copy of the "backup.tgz" (hoooorah!) and in "info" is a file called "backup.tgz.trashinfo." I'm going to LEARN from my mistakes this time!!

How should I go about removing these files? Should I just "gksudo nautilus" to this location and delete them myself? Or is there a better way to go about this

Honestly, I'm not sure if it's the right way but I ususally just delete the .Trash folder. Gets recreated for me when I delete new things.

---

