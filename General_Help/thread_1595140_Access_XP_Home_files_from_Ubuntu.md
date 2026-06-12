---
title: "Access XP Home files from Ubuntu"
date: 2010-10-12
forum: General Help
---

### Post by zaino22 on 2010-10-12
I have XP Home edition that was not activated within time, and is locked unless I enter Product key. Since I do not have Product key, Microsoft cannot help me with activation. I have important data that is very near and dear to me stored on this machine. I tried SAFE MODE but it does not work, going to CTRL+U from 'Lets's activate' window, and clicking on internet explorer to access files did not work either. I have good Media Center Edition copy, which I can install but data will be lost after installation so I want to archive the data first. 

Can I boot from Ubuntu Boot CD, and access my XP documents/PIX and copy it over to storage device before I reinstall XP Media center? 

Any help will be appreciated.

Thanks,
Zaino22

---

### Post by arkadios on 2010-10-13
I'm pretty sure it's Windows+U to open Narrator and then click *Microsoft Web Site* to launch IE. Using a LiveCD and mounting the drive/partition should work.

---

### Post by zaino22 on 2010-10-13
For some reason IE doesn't open from Narrator window and just seem it is hung by a process. What's live cd? 
Can we not access the file via ubuntu bootable Cd ?

---

### Post by Refalm on 2010-10-13
Ubuntu Boot CD = Ubuntu Live CD

---

### Post by Mark Phelps on 2010-10-13
When you boot from an Ubuntu desktop CD, it will present you two options -- Try or Install.  The "Try" option is what we generally call the LiveCD mode.  That will run Ubuntu in memory and NOT install it to your PC.

You can then plugin a USB stick or drive, select your XP Home partition in Places, and copy the files off.

---

### Post by zaino22 on 2010-10-13
Amazing. you guys are the best... i will try it and let you know if it worked, and then we can mark this topic SOLVED. 
 
This Laptop has my wedding, honeymoon, and all the good memories PIX, my wife would have killed me for not having the backup... ;)

---

### Post by zaino22 on 2010-10-13
Just one more thing before I go home and try it, does it mean I can access NTFS partition (because that's what my Hard Disk is) via Ubuntu Live CD? if yes, my documents/pix are located under my Admin USER account, can I access those as well even though those Folders are not Shared Folders?

---

### Post by oldfred on 2010-10-13
One of the real dangers of knowing Linux. You can do anything on the windows partition (including damaging it), if you have direct access to it. Default mount may be read only, so if you do have any issues you may have to manually mount it with full permissions as NTFS partition permissions are only set on mount.

But you should be able to easily copy all your data especially if you know the location(s) as windows often put stuff all over the place. 

I normally try not to write into my working XP install, just to avoid an accidental delete of something vital. I do read from it without issue, but use a shared NTFS partition for most data.

---

