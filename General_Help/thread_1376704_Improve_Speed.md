---
title: "Improve Speed?"
date: 2010-01-09
forum: General Help
---

### Post by Cola_Cartel on 2010-01-09
I'm running Karmic on a 3-yr old Dell Latitude D520 laptop with 502 MB RAM, and 2 1.66 GHz CPUs. I'm presently dual-booting, Linux has a 15 GB partition of a 50 GB hard-drive it shares with Windows XP.

At present, however, Ubuntu becomes mind-numbingly slow any time I try to multitask. This was most irritating when I was trying to keep .pdf files open on Evince for references for a paper I was writing on Open Office, but the screen seems to keep graying out when I do so much as surf on a second tab on Firefox, or try to browse the web with Pidgin running.

Any suggestions on how I can get Ubuntu running cleanly again? Is this the sort of performance I should be expecting from Karmic given my specs or should I be able to get better speed?

---

### Post by jocko on 2010-01-09
I guess you would fix it by adding more ram. Next time it happens, open up a terminal and run this:
```
free -m
```
It gives you an output similar to this:
```
jocko@jocko-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1508       1469         38          0         32        973
[COLOR=Blue]-/+ buffers/cache:        463       1044[/COLOR]
Swap:         4996          0       4996
```
The important part is the "-/+ buffers/cache"-line.
This output was from when I ran ubuntu (gnome) with firefox showing only this page, an empty document open in open office writer, a small pdf file open in evince and audacious playing an mp3, and that uses up 463 Mb ram.
If I only had 512 Mb ram, that would mean my memory would be almost completely full when I do essentially nothing, and would force the os to swap data back and forth between the swap partition and ram, causing severe slow-down and recurring freeze-ups of the running applications every time an application needs something that has been swapped out to the hard drive.

Another option is to run a more light-weight gui instead of gnome, and a more light-weight word processor than the open office one.

---

### Post by Jackzor on 2010-01-09
Try adding swap? (if you didn't already)

Creating a file for 512 MB size you want: 

We will create a /mnt/512Mb.swap swap file.
```
sudo dd if=/dev/zero of=/mnt/512Mb.swap bs=1M count=512
```

Formatting that file to create a swapping device: 

```
sudo mkswap /mnt/512Mb.swap
```

Adding the swap to the running system:

```
sudo swapon /mnt/512Mb.swap
```


Making the change permanent: 

Edit the /etc/fstab: 


```
gksudo gedit /etc/fstab
```



Add this line at the end of the file: 


```
/mnt/512Mb.swap  none  swap  sw  0 0
```



Post back if this helps!

---

### Post by ZeroSpawn on 2010-01-09
Check your Start up programs, and get rid of all the ones that you don;t use. I have a Dell 610/512mb/1.66Mhz and after I checked my startup the speed has went UP! And tweak your firefox.

---

