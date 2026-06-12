---
title: "Sharing between pc's with ubuntu 12.04"
date: 2012-06-09
forum: General Help
---

### Post by techieguy_100 on 2012-06-09
OK, I've been using ubuntu for a long time, really like it, today I installed ubuntu 12.04--not liking it. I finally have all my pc's on my network showing up, but I cannot see any file shares on my windows or linux boxes. I did install my network printer which is shared on a windows pc. My other ubuntu box 10.04, has no issues with any of my shares except the ones I have created on my 12.04 linux.  12.04 going to 10.04, I can see the computer but none of the shares. 10.04 going to 12.04, I can see the shares but can't open them.  12.04 cannot 'see' any of the windows or linux shares.  I'm confused.  Can't say I like this new interface either, much harder to find anything. It's becoming more like windows all the time.

---

### Post by deadflowr on 2012-06-09
Assuming your running samba, and all your configurations have been set as you would like. Did you do a reboot? As I found that usually works.

---

### Post by techieguy_100 on 2012-06-09
rebooted several times, I can live without samba working properly and can troubleshoot that at my leisure, the more important issue here is accessing some files on my ubuntu 10.04 box the message is "unable to mount location failed to retrieve share list from server"

---

### Post by techieguy_100 on 2012-06-11
any ideas folks?  I'm accessing my files now just fine between the two linux boxes, and my windows machines are able to access files on both of my linux boxes, but I still cannot access any shares on my windows machines from ubuntu 12.04

---

### Post by timcowchip on 2012-06-11
Gigolo. Its in Miscellaneous - Graphical (universe).

---

### Post by SleepWalkerX on 2012-06-11
> 10.04 going to 12.04, I can see the shares but can't open them.

What error do you get?

Also, can you connect directly to the computers through smb://x.x.x.x in nautilus and see the shares?

---

### Post by techieguy_100 on 2012-06-11
Linux access is solved, when accessing windows shares from ubuntu 12.04, I get the following message " Unable to mount location, Failed to retrieve share list from server"

---

### Post by techieguy_100 on 2012-06-13
problem solved: stupid typo!!  apparently it helps to put in the right ip address, feeling a little sheepish about now...

---

