---
title: "Problem with File Manager"
date: 2010-02-13
forum: General Help
---

### Post by hakermania on 2010-02-13
Some times the File Browser is not responding and I do him force quit. Although if I do this  cannot open any directory and my Desktop looks like empty. Although I can start any processes.So, I would like to know if there is any terminal-command in order to start again the File Manager. 

Thx, running in Ubuntu 9.10

---

### Post by Tourdog on 2010-02-13
hakermania,

Do you mean:  In Terminal  type "gksu nautilus"  Enter, then  key in your password when prompted and your file browser will come up.

HTH  :)!

---

### Post by hakermania on 2010-02-13
Thx for the answer but unfortunately it shows the following message:
** (nautilus:6575): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:6575): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:6575): WARNING **: No marshaller for signature of signal 'ShareCreateError'
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
Initializing nautilus-gdu extension

and then a new window of the File Browser pop-ups in /root directory buts it turns grey in a few seconds, which means that the program is not responding. Additionally, I still cannot see my desktop and I cannot open any other File Browser window and browse my files.Any other ideas?

---

### Post by hakermania on 2010-02-14
Any suggestions plz!
It is a real problem!

---

### Post by Zidaps on 2010-02-19
I am having the same problem. I was trying to follow a thread on how to configure my samba correctly, and upon doing: 

> sudo apt-get install winbindit froze when it was trying to start winbind. 

I cannot use synaptic, because its telling me that some other process is using it (It was the "apt-get" from winbind in terminal. synaptic suggested I try the following:
> sudo dpkg --configure -a
After some time I restarted the system. Samba and winbind were not allowing boot to happen. So I used a live cd and removed samba and winbind from /etc/init.d and now that I am able to log in again, There are no icons on my desktop, I cannot open or mount any drives without them freezing and crashing. Whenever I try to restart, it says that "file manager is not responding"

Oh and I have no internet connection for some reason so I cannot use synaptic to re-install nautilus or anything else that requires an internet connection. I had an internet connection before all of this happened, and I am typing this from within the same network, same internet connection, so my internet is fine.

Anyone know what could be causing this, and how I can fix this ?

---

### Post by joegreat on 2010-03-22
> **Zidaps said:**
> Anyone know what could be causing this, and how I can fix this ?
Hi,
I have the same issue. Do you have any news/update to solve the problem?

With kind regards
Joe

---

### Post by afrodeity on 2010-03-26
Apparently sudo apt-get remove frei0r-plugins will fix the problem.

[https://bugs.launchpad.net/ubuntu/+source/opencv/+bug/459940](https://bugs.launchpad.net/ubuntu/+source/opencv/+bug/459940)

I haven't tried this yet.

---

### Post by monzta on 2011-06-20
Hi,

I installed Thunar and made it the default file manager and now the system is fine. Guess its a problem with File Manager

---

### Post by monzta on 2011-06-20
I installed Thunar and made it the default file manager. Looks like that fixed the problem

---

