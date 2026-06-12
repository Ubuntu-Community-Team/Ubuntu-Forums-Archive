---
title: "Ubuntu 12.04 System &quot;Stops&quot; When booting into Recovery Mode"
date: 2012-10-04
forum: General Help
---

### Post by jedd999 on 2012-10-04
I have a bit of a problem, and help would be greatly appreciated!
When I try to boot into **recovery mode**, the system will pause where it says "Begin: Running /scripts/init-bottom ... done." and it will be paused there indefinitely.
 
If I press alt+F7, it will take me to the command prompt and the system will apparently be functioning fine (I sort of figured that out from doing some keyboard mashing). 
 
Following is some set-up information: 
1) I am using Ubuntu 12.04 desktop edition
2) I have remove "friendly-recovery" so that I dont have to select "root" when I chose to boot into recovery mode
3) I have modified the /etc/default/grub file a little bit (since there are multiple OS on the hard drive): 
[FONT=Calibri][SIZE=3][FONT=Calibri][COLOR=dimgray]   GRUB_DEFAULT=**saved**[/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][FONT=Calibri][COLOR=dimgray]**   GRUB_SAVEDEFAULT=true**[/COLOR][/FONT][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][FONT=Calibri][COLOR=dimgray]**   #**GRUB_HIDDEN_TIMEOUT=[/COLOR][/FONT][/SIZE][/FONT]
[SIZE=3][COLOR=dimgray][FONT=Calibri][FONT=Calibri]   GR[/FONT][/FONT][FONT=Calibri][FONT=Calibri]UB_HIDDEN_TIMEOUT_QUIET=**false**[/FONT][/FONT][/COLOR][/SIZE]
4) I have done all the auto-updates through the update manager
 
Other than that, its basically a fresh install... 
 
**Any thoughts on why this issue might be happening? **

---

### Post by jedd999 on 2012-10-09
Anyone able to help?

---

### Post by jedd999 on 2012-10-15
?

---

### Post by grahammechanical on 2012-10-15
This I think is the cause of your problem:

> I have remove "friendly-recovery" 

We we boot normally the boot manager sees this in the boot script

> ro quiet splash

When we select recovery mode the boot manager see this

> ro recovery

But your have removed the utility that is supposed to load with the recovery instruction.

Regards.

---

### Post by jedd999 on 2012-10-15
> **grahammechanical said:**
> This I think is the cause of your problem:
 
 
 
We we boot normally the boot manager sees this in the boot script
 
 
 
When we select recovery mode the boot manager see this
 
 
 
But your have removed the utility that is supposed to load with the recovery instruction.
 
Regards.
 
I dont think that can be the problem, because on some systems this will work fine, while on others there is still a problem... it seems to be intermittent. 
the entry for recovery mode still shows "ro single nomodeset"

---

### Post by jedd999 on 2012-10-15
how can I check exactly what is happening when the shell is hanging up as it is...?

---

