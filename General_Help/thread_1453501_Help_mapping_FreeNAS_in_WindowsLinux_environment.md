---
title: "Help mapping FreeNAS in Windows/Linux environment"
date: 2010-04-13
forum: General Help
---

### Post by JavaBeanHead on 2010-04-13
Hi all . . . 
 
I've found that simply sharing a folder on my Ubuntu PC with other Linux PC's on my network proves unwieldy from an 'ownership' standpoint. For example, if I create a file from my Ubuntu Laptop and save it onto my Ubuntu Desktop 'share', I find that if I try to access it from the Desktop that the group/ownership prevents my access so I end up having to chown it. 
 
I'm finding sharing in a mixed environment to be a pain.
 
So, I recently configured an old desktop box with FreeNAS and I want to move all of my files from my main Ubuntu PC over to it, and have those files accessible from various clients (both Windoze and Linux) from thoughout my network. Now I've got the FreeNAS all set up and shared, and I'm ready to transfer files to it. 
 
What's the best way to mount Mr. FreeNAS on my various desktops and laptops such that sharing is not a problem from a security (group/owner) standpoint? Should I be using CIFS/SAMBA or is NFS mounting better? Will there be sharing problems or ownership issues when accessing from Windows?
 
The more detailed you could be, the better - relatively new at this stuff.
 
Thanks in advance!

---

### Post by JavaBeanHead on 2010-04-14
*bump*

---

### Post by JavaBeanHead on 2010-04-15
Answering my own question, I think:
 
[http://ubuntuforums.org/showthread.php?t=1025045](http://ubuntuforums.org/showthread.php?t=1025045)

---

