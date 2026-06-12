---
title: "Win 7 X64,cannot boot ubuntu with wubi"
date: 2009-12-31
forum: General Help
---

### Post by flyfar on 2009-12-31
Hi,I installed ubuntu with wubi last month,my system is win7,x64;
**[COLOR=red]I used it very well all these days[/COLOR]**,but today when I boot ubuntu,it shows:
 
NTFS...:nowubildr
NTFS...:nowubildr
NTFS...:nowubildr
...CANNOT FIND CRLDR...
 
I search for this problem,they say I should use a new grldr.mbr in drive C and boot.ini, but you know in WIN7 ,there isn't boot.ini file for booting.
 
How to resolve this?I don't want to reinstall 'cause there are some data files in my ubuntu.

---

### Post by flyfar on 2010-01-01
no body knows...

---

### Post by garvinrick4 on 2010-01-01
Run bcdedit in command line of 7 and see if there is  a menu item  in there with a Wubi in
it.

---

### Post by Leppie on 2010-01-01
Sorry, I am not familiar at all with wubi installs and to be honest would never advice anybody to use this method.

That said, when booting from the livecd, try locating the files:
```
\ubuntu\disks\root.disk
\ubuntu\disks\boot
```
on your windows partition.
if they are not in the indicated locations, try looking for them in the found.XXX folders. apparently windows like to move these files from time to time.

---

### Post by flyfar on 2010-01-03
I found in my win7,under the 
\ubuntu\disks\boot
there is no grub.cfg file,is that win7 wiping it out?
my ubuntu is 9.10
how could I do,I'm a newbie,ths

---

### Post by pro003 on 2010-01-03
hi, since you're a newbie I won't even try to help you by telling you how could you resolve your problem in a manner that it should be solved. 

instead I will tell you that best possible and most effective solution for 'a newbie with a dual boot problem' is getting 'super grub' cd. google it and you should be able to download it and burn it in matter of minutes, boot it and then just follow on screen help, it will guide you nice and easy to the end of your problem. and let's say hopefully. 

if that fails, will try some' else....

---

### Post by Leppie on 2010-01-03
> **flyfar said:**
> there is no grub.cfg file,is that win7 wiping it out?
my ubuntu is 9.10
how could I do,I'm a newbie,ths

as i wrote previously:
> **Leppie said:**
> if they are not in the indicated locations, try looking for them **_in the found.XXX folders_**. apparently windows like to move these files from time to time.

---

### Post by MichealH on 2010-01-03
I wouldn't recommend using wubi.exe because when you install it using the live cd I find I is more stable. Make sure windows is installed first when installing form live cd!

---

### Post by flyfar on 2010-01-03
Thank u,but there isn't found.xxx directories in WIN7.
I'd like to burn the super grub disk for a try:P
> **Leppie said:**
> as i wrote previously:

---

### Post by pro003 on 2010-01-03
> **flyfar said:**
> Thank u,but there isn't found.xxx directories in WIN7.
I'd like to burn the super grub disk for a try:P

just to remind you, you should first try to 'boot partition' of course first by selecting gnu/linux advance and boot partition and then boot partition which is of course ext4, if you have made it to load ubuntu in that way, then reboot and do the same now for windows/advanced/boot partition/hda# ntfs... and if you made it to load win 7 restart and then try to install grub or update it, there is an option to install lilo as well....

---

