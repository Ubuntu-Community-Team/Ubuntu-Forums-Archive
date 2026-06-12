---
title: "Enabling restricted driver and mounting hdd in live cd"
date: 2009-10-17
forum: General Help
---

### Post by tom.swartz07 on 2009-10-17
Hi all, 

I have just a basic question- I'm in a bit of a pickle. I'm running karmic on live cd, and I need the 'admin password' to enable my restricted wireless card driver. What is the password? Is there a terminal command that will accomplish the same effect?

Also, if anyone has any idea why my HDD isn't being recognized by the live cd, I would GREATLY appreciate some input. The main explanation of this problem is here:[http://ubuntuforums.org/showthread.php?t=1292805](http://ubuntuforums.org/showthread.php?t=1292805)

thanks! I really appreciate the help. 
Tom

---

### Post by hal10000 on 2009-10-17
> I need the 'admin password' to enable my restricted wireless card driver. What is the password?

The live-cd has no password, just hit ENTER

> Also, if anyone has any idea why my HDD isn't being recognized by the live cd

open a terminal window and post the output of the following commands:
```
sudo fdisk -l
```
and 
```
lspci
```

Also perform this:
```
sudo lshw | less
```
As it produces a very long output, you should only the relevant parts (those concerning your sata controller, mass storage and disk

---

