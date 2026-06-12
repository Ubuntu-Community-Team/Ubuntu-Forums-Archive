---
title: "serious memory misallocating in 10.10"
date: 2010-11-13
forum: General Help
---

### Post by elmoosecapitan on 2010-11-13
Hi All,


So I have two problems I believe are related because they both appeared about a week after I first installed 10.10 (Installation date was end Oct/beginning Nov).

1. I have a home folder icon on my toolbar. Every time I click it Rhythmbox opens. Right-clicking the icon and checking out my properties I get read exactly what anyone would expect to get to access one's home folder.

2. 3 out of 4 times I boot 10.10 catches serious disk errors. Running fsck manually, I see that an obscene number of inodes have been misallocated and need to be reassigned. Free blocks are also being miscounted.

2.a. Post-disk error cleanup, 10.10 does not recognize my computer's name and sets it to the default "localhost"
2.b. Some personal settings are lost but are recovered after a reboot. For example, default firefox homepage is set to "http://start.ubuntu.com/10.10/Google/".


Potentially useful information: Linux version 2.6.35-23-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #37-Ubuntu SMP Fri Nov 5 19:16:29 UTC 2010

---

### Post by Toxicbits on 2010-11-13
Could it be that the reason for your first problem is that folders are assigned to Banshee? You could fix that with Ubuntu Tweak

---

### Post by elmoosecapitan on 2010-11-13
actually, i do not have banshee installed.

---

### Post by elmoosecapitan on 2010-11-13
Sorry, i am pushing this back to the top in case someone who can help with 2 is currently on the forums.

---

### Post by elmoosecapitan on 2010-11-14
bump

---

