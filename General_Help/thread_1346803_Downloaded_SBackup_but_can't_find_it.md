---
title: "Downloaded SBackup but can't find it"
date: 2009-12-05
forum: General Help
---

### Post by mahoopes on 2009-12-05
[SOLVED]  Hello, I am a new Ubuntu user.  I enabled downloads from the "Universe" repository and downloaded SBackup.   The Help instructions are to press System --> Administration --> Simple Backup Config, but the latter is not presented as a choice under Administration.  Any advice?

Thanks,
M.A.Hoopes

---

### Post by ranch hand on 2009-12-05
You may need to reboot or at least restart X.

---

### Post by mahoopes on 2009-12-05
Thanks Ranchhand.  I tried rebooting but it made no difference. 
MAH

---

### Post by bobcollard on 2009-12-05
> **mahoopes said:**
> Hello, I am a new Ubuntu user.  I enabled downloads from the "Universe" repository and downloaded SBackup.   The Help instructions are to press System --> Administration --> Simple Backup Config, but the latter is not presented as a choice under Administration.  Any advice?

Thanks,
M.A.Hoopes
You should find it under the System/Administration menu and it is called Simple Backup Config and Simple Backup Restore.  You have to use Config first so when you restore it will know where to look for your files.

---

### Post by mahoopes on 2009-12-05
Thanks Bob, 
In Downloads I see the following:

SBACKUP.DESKTOP
SBACKUP-CONFIG.PNG
SBACKUP-RESTORE.PNG

But I can't run them via either double clicking or right clicking.  Do I need to use command line?

M.A.

---

### Post by bobcollard on 2009-12-05
> **mahoopes said:**
> Thanks Bob, 
In Downloads I see the following:

SBACKUP.DESKTOP
SBACKUP-CONFIG.PNG
SBACKUP-RESTORE.PNG

But I can't run them via either double clicking or right clicking.  Do I need to use command line?

M.A.
I thought you had already installed them?  Did you get them from the Internet as packages?  Perhaps with ,gz or .zip on the label?  It is much simpler to go to menu System/Administration/Synaptic Package Manager and get the whole thing in one package installed automatically.   In the search entry of Synaptic type "sbackup"  (without the quotes)  Mark it for installation, click Apply and follow the instructions.  Then you will find it where I told you before, already installed.

---

### Post by ranch hand on 2009-12-05
Yup, I think you ought to try installing it.

The last two on your list should open for you in an image viewer because that is what they are.  .PNG is another format like .jpg.

---

### Post by mahoopes on 2009-12-05
That did it!  Thanks -- I went through Synaptic originally, but must have dome something wrong.  Appreciate your help.

---

### Post by bobcollard on 2009-12-05
> **mahoopes said:**
> That did it!  Thanks -- I went through Synaptic originally, but must have dome something wrong.  Appreciate your help.
You are welcome.  Now, if you would, please, return to your first entry and edit the Title by adding <Solved> to it, so other people can perhaps get something from it.  Good luck.

---

