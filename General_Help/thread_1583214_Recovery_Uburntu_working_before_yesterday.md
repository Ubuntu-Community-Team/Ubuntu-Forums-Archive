---
title: "Recovery Uburntu working before yesterday"
date: 2010-09-27
forum: General Help
---

### Post by filsdepapa on 2010-09-27
Hello all,
 
I installed Asterisk software on Uburntu 10.4 and don't have any problem about Asterisk. It was working well before I updated yesterday, Sunday, September 26,2010 some Uburtu kernels.
 
Once updating some news software and Kernels, Asterisk is working, but rejected my Voip phone services. My system is not connected also my phone provider. Both are disconnected.
 
What I need is to recovered my system only from yesterday to the past, not since I have updated to today. What I can do?
 
Any body can help me?
 
Thanks

---

### Post by andrewthomas on 2010-09-27
Look in /var/log/dpkg.log to determine what packages were updated.
Go to /var/cache/apt/archives/ and downgrade to the previous version of packages that were updated.

---

