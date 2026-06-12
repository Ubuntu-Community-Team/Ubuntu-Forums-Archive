---
title: "Ubuntu 11.04"
date: 2011-04-17
forum: General Help
---

### Post by chand.sethi77 on 2011-04-17
I have ubuntu 10.4 and I am too much excited about ubuntu 11.04. 
The thing I wanted to ask is if [B]I COULD UPGRADE TO 11.04 WITHOUT DOWNLOADING AND INSTALLING IT AGAIN
 [/B]How to do that. Please tell me 
Thanks!

---

### Post by thenickrulz on 2011-04-17
no you have to download it....

---

### Post by K_45 on 2011-04-17
Here:

[http://www.addictivetips.com/ubuntu-linux-tips/how-to-upgrade-to-ubuntu-11-04/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-upgrade-to-ubuntu-11-04/)

---

### Post by sanderd17 on 2011-04-17
In the past, I've had serious problems with the update manager method. And it seems that 11.04 isn't going to work on my system.

This is what I find the safest method to upgrade (but always do a complete backup):

[LIST]
[*]repartition your hdd so that the Linux part is split in 2 times about 15GB for the OS and you can use the rest as your /home partition. Look here for how to make a separate /home partition: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[*]the result should be that one 15GB partition has Ubuntu on it and the other 15GB partition is "unallocated"
[*]now you download and burn the new ubuntu live CD
[*]install the new ubuntu on the empty 15GB partition
[/LIST]

This way, you will still have your old OS (in case the new ubuntu isn't compatible). When you upgrade again, you can just overwrite the 15GB partition of your old OS.

for the record:
I started with ubuntu 8.04, that worked good, just as 8.10. But ubuntu 9.04 and 9.10 were disasters for me. It took me a complete week to get them running. 10.04 and 10.10 just were perfect again, I really had no bugs. But now, I tried the beta 1 and beta 2 of 11.04 and I'm not able to get past a grub screen. It looks like I have a problem with odd years :-P

---

### Post by 3rdalbum on 2011-04-17
You can either dist-upgrade to 10.10 and then to 11.04, or the smarter method: Download and burn 11.04, run the installer and choose the "Upgrade" option. It preserves your home directory and downloads new versions of your current packages. Note that you should remove any packages you don't want before running the Ubuntu CD, and it's safe to force quit the installer while it is getting your old packages updated.

---

