---
title: "Windows network drive not displaying all folders in Ubuntu"
date: 2011-04-07
forum: General Help
---

### Post by CrusaderAD on 2011-04-07
When I map a windows 7 network drive in ubuntu, it doesn't display all the folders on the shared drive. I checked permission settings and all looks ok. I can connect from a windows machine and see all the files. Any ideas?

---

### Post by CrusaderAD on 2011-04-08
Bump

---

### Post by Zwan on 2011-04-08
Try re-applying the security settings via windows. Maybe it didn't finish or you cancelled it?

---

### Post by CrusaderAD on 2011-04-08
I tried that. It's strange... I can ftp into the folder with the same user and I can see everything. It must be a samba issue.

---

### Post by rl78 on 2011-04-14
I am having the same issue connecting to folders on my Vista Ultimate Box. 
I recently attempted to encrypt about 70GB of pictures and movies and it froze in the process. I canceled it, and still had to uncheck the box to decrypt files. Everything appears normal from Windows locally, but I can't view the whole folder. I can get there by typing the path however on my Ubuntu LT. Nothing is hidden. Samba installed, user account configured with same Ubuntu and Windows user and pw. 

This is a fresh install of Ubuntu 10.10 and updated. I am pretty sure it was fine prior to my fresh install and prior to me attempting to encrypt the folder but nothing is currently encrypted.

---

### Post by rl78 on 2011-04-14
I have solved my problem, and there seems to be a limit to how much data nautilus will show you in a given folder. I divided my directories to divide the amount of data per folder and everything is visible. 
I tend to think this will we be an issue with network folders/shares. I don't have any local directories on my LT running Linux  that big to even test it at the moment. I didn't see an option in nautilus to manipulate the amount of data you can view, only in regard to the preview of files you can see locally or networked. 

I will post back if I find more specific information.

---

### Post by CrusaderAD on 2011-04-14
Thanks for the update! I'll take a look around too now that I have a lead. Good work! Let me know what you find. I'll post any updates as well.

---

### Post by rl78 on 2011-04-17
Lets us know if the information in this thread solved your problem. If so, mark is as solved as well. 

Thanks, and your welcome.

---

### Post by CrusaderAD on 2011-04-17
> **rl78 said:**
> Lets us know if the information in this thread solved your problem. If so, mark is as solved as well. 

Thanks, and your welcome.

I dont mean to sound rude, but why would I thank you for that? Please don't go around stating the obvious. It doesn't help. I'm not exactly a newbie to the forums.

---

### Post by rl78 on 2011-04-17
> **CerealCypher said:**
> Thanks for the update! I'll take a look  around too now that I have a lead. Good work! Let me know what you find.  I'll post any updates as well.

I was saying your welcome to your earlier post because you did say thank  you. I am not soliciting any thank yous. What I did ask is did the information help you? 

> =but why would I thank you for that?

I don't know, why did you thank me for that?

---

### Post by CrusaderAD on 2011-04-17
lol sorry! I just woke up. I forgot you were the original responder. No pun intended!

---

### Post by DisturbedDragon on 2011-04-17
Good day.  I have had this same issue on Ubuntu and openSuse systems using Thunar and Nautilus.  I have a Windows 7 server which hosts all my network shares via a 5TB RAID5 since the mobo has nvraid which is easily managed under Windows. Particularly in my movies folder I noticed when accessed from any Linux PC, Android phone, or through my Orb web GUI folders were missing.  The problem is too broad to be a client issue.  I unmounted the array and performed a disk check.  Windows said no errors were found, but when I remounted the array after the check, Voila!, all folders show up on all systems and the Orb web GUI.  I suspect a bug in the MFT, but will probably never know.  Thanks M$!  Currently looking for a hardware RAID controller supported by openSuse.

---

### Post by DisturbedDragon on 2011-05-04
Found another subject of interest.  I have found this problem on Ubuntu, XBMC, openSuse and lots of other sites.  Thought it was only a Linux/MAC issue but I recently had the same issue on my tablet running XP Tablet Edition (x86), fully updated.  Also, if the entire directory structure does not show up then sub folders with multiple files will not show entire contents either.  Problem is definitely in Win7 (Pro x64 for me).  Unmounting and remounting drive worked for about a day, nothing else has including drive checking and reconfirming share status and permissions.  Not sure what to attribute this bug to other than Winders is Winders ;).  Will keep looking for a solution though.

---

