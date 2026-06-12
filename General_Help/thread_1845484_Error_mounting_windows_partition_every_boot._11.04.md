---
title: "Error mounting windows partition every boot. 11.04"
date: 2011-09-17
forum: General Help
---

### Post by yonni on 2011-09-17
Hi,

I have Ubuntu 11.04 & Windows 7 installed on the same disc, with all of my data on the NTFS partition so that I can get at it from both OSs. Is set up the following line in fstab to mount the windows partition on boot since if I log in without it mounting all of my links to the directories where my stuff is stored will break and Clementine will have a hissy fit 'cause it can't find my music.

Every time I restart during the boot process I get an error stating that it could not mount the windows partition and giving me the option of dropping into a root terminal to do this manually, which I can do. Then it works fine for that session. I just don't want to have to drop into a terminal every boot just to enter 'mount /dev/sda2 /media/windows'

The line I added to fstab was:
```
/dev/sda2				  /media/windows  NTFS	  rw,suid,dev,exec,auto,user,sync	0	0
```
I'm assuming for some reason it doesn't like the options there, which is why it's failing. What've I done wrong?

P.S. is there a more elegant way to achieve this? Surely ubuntu should've moved on to having a system setting to "automatically mount this drive" by now? I would have assumed just being able to right click on the drive and instead of selecting "mount" select "always mount this drive".

---

### Post by dcstar on 2011-09-17
> **yonni said:**
> 
.........
P.S. is there a more elegant way to achieve this? Surely ubuntu should've moved on to having a system setting to "automatically mount this drive" by now? I would have assumed just being able to right click on the drive and instead of selecting "mount" select "always mount this drive".

It already has, install the **pysdm** package and use that.

---

### Post by Morbius1 on 2011-09-17
> /dev/sda2  /media/windows [COLOR=Blue]** NTFS**[/COLOR] rw,suid,dev,exec,auto,user,sync    0    0> Every time I restart during the boot process I get an error stating that  it could not mount the windows partition and giving me the option of  dropping into a root terminal Because there is no filesystem type: [COLOR=Blue]**NTFS**[/COLOR], it's [COLOR=Blue]**ntfs**[/COLOR] - small case. You know how persnickety Linux can be about capitalization:
```
/dev/sda2  /media/windows ntfs rw,suid,dev,exec,auto,user,sync    0    0
```For future reference:

* Anytime you edit fstab you should unmount the partition if you mounted it manually and run the following command:
```
sudo mount -a
```That command will test for errors and mount the partition with the edited fstab line without doing a reboot so you can fix it earlier.

* > Surely ubuntu should've moved on to having a system setting to "automatically mount this drive" by now?You are given an opportunity when you originally installed the OS to have the installer do all this for you. It asks you what partition you want to automount, what it's filetype is, and where you want it to mount.

---

### Post by yonni on 2011-09-19
Thanks for that, sorry I was being so stupid

> **Morbius1 said:**
> 
...
* You are given an opportunity when you originally installed the OS to have the installer do all this for you. It asks you what partition you want to automount, what it's filetype is, and where you want it to mount.

Do you mean in the bit of the installer for organising partitions/swapspace/formatting etc. 'cause I'm really not very comfortable touching my windows partition at all with that in case I make a mistake and have it formatted by accident. Not only that, but there are many other reasons for wanting an "automount this drive" - e.g. having bought a new drive, it's just an intuitive thing to have, changing your mind post-installation.

I just don't think that's much of a solution/alternative.

---

