---
title: "Use external Hard Drive for Virtual Box hard drive"
date: 2011-06-03
forum: General Help
---

### Post by Joe- on 2011-06-03
I have a laptop with only 30GB storage and I want to install Lubuntu in virtual box but Lubuntu needs 5GB of storage space which i dont have. Could i use an external 160GB hard drive to act as the hard drive for the virtual machine without affecting the files that are already on the external hard drive?

Cheers

---

### Post by t0p on 2011-06-03
Yes, you can find where to add the drive in Settings in VirtualBox.  Unfortunately I'm not at my VBox-running machine right now, so I can't be more specific.  But basically make a new directory on the external hard drive; then in VirtualBox settings, make that directory as your hard drive.  I've done it myself, and it was an easy procedure.

---

### Post by Joe- on 2011-06-03
So it wont affect all the files that i have on the drive already? its not going to format it in anyway?

---

### Post by wolfgangmcq on 2011-06-03
It shouldn't, if you specify a sub-folder.

Semi-tangental: Do you have a backup of the files on the HD? I suggest backups for everything, no matter what. This is especially true in UNIX, where a space can accidentally delete everything, as in rm / home/user/junk.

---

### Post by MartyBuntu on 2011-06-03
You can use another drive to install virtual machines if you wish.
Just make sure the drive is mounted when you install and access it.

---

### Post by Joe- on 2011-06-03
Im going to copy all the files on the HD to my Win7 pc and then try and set it as the Virtual Box OS and if anything does go wrong il still have the files. il report back here.

Cheers for the help guys.

---

### Post by Joe- on 2011-06-04
Works fine, i just created a folder called OS on the external HD and set that as the VB HD. The install took a while but Lubuntu seems to be running pretty quick. 

Cheers for the help.

---

