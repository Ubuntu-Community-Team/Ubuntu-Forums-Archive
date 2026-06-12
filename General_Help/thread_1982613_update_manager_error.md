---
title: "update manager error"
date: 2012-05-18
forum: General Help
---

### Post by chipvan on 2012-05-18
I was staying at hotel and tried to update 12.04 before I was logged on local service.  It returned a critical error.  now synaptic package manager and update manager quit working.  I have a red circle with white dash on my tool bar.  If it helps, I can post entire error.

any help would be great.

---

### Post by wilee-nilee on 2012-05-18
Generally the first command will unlock stuff and the second restart anything stopped that was running use with care.

Do not upgrade without a backup, a clone if possible, you have to consider losing everything at any time always.

  	 	 	 	 	 	   [FONT=Verdana, sans-serif][SIZE=1]sudo dpkg --configure -a [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo apt-get -f install [/SIZE][/FONT]

---

### Post by chipvan on 2012-05-18
thank you.  i will try it
I looked up the commands that you gave, and found a list of steps to backup and correct problems with update manager.  Your help was invaluable.  
problem resolved.


Thank you again

---

