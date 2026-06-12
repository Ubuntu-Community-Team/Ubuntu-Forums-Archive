---
title: "I cannot download ANY software through &quot;add/remove&quot;, or manually...."
date: 2009-10-06
forum: General Help
---

### Post by earth.to.justin on 2009-10-06
Please help. I installed Ubuntu Desktop 9.04 "Jaunty" on my machine, and the install went fine and I was able to update and add software/applications/(whatever the correct ubuntu terminology is) for about two days. Now I cannot use the Applications -> Add/Remove feature for updating or removing and adding new software programs. I also cannot use the System -> Administration -> Software Sources window to use third party software like Wine. Finally, I cannot manually download programs likes Adobe Flash. I can get the file from their site, but when I try to unpack and install it, I cannot. 

ALL of these problems give me the exact same error message:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can some one explain how to manually run this?


Thanks for your help
Justin

---

### Post by fluffman86 on 2009-10-06
Go to Applications > Accessories > Terminal and type:
sudo dpkg --configure -a

---

### Post by umaroxx on 2009-10-09
> **fluffman86 said:**
> Go to Applications > Accessories > Terminal and type:
sudo dpkg --configure -a

Hi fluffman86,
I have the same problem as earth.to.justin. So I entered 'sudo dpkg --configure -a'
Then the message

'Adding extension /usr/lib/openoffice/basis3.0/program/mailmerge.py...' (Cursor blinks)

showes up and nothing else happens. The process runs for hours. No applications can be started anymore. It seems as if the PC is frozen.

Any suggestions how solve the problem?

---

