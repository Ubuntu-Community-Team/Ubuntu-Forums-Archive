---
title: "Wow ubuntu crashed and i cant boot it back up"
date: 2010-12-24
forum: General Help
---

### Post by drswingingblades on 2010-12-24
-------Backgroun info------------
I had Vuze open (and torrenting) and I had a half baked program in monodevelop running.
 
I had to do some shopping for christmas, I was gone about 6 hours.
 
 
----------The Problem-------------------
I came back and after i woke the screen up from sleep, the screen froze. So I was patient and I took a shower. I came back and it was still frozen.... I clicked the mouse once and then my screen had a seizure so I held the power till it turned off. Now I try to boot into Ubuntu (10.10) and ABSOLUTELY NOTHING happens. I just get an empty black screen.
 
 
--------Concern of a new Ubuntu user-----------------
I'm hoping this isnt a normal thing? Cause im just switching to Ubuntu about a week ago. and i wouldnt be very happy if i had to deal with this
 
 
------What i can still do----------
I can boot into windows7 still cause i have 2 hard drives. But i obivoussly cant acces the ubuntu hdd.
 
I'll re install if i have to but im going to lose ALOT of Papers and c++ programs and being in college its kind of crucial for me to have these
 
 
 
 
PLEASE HELP

---

### Post by noah++ on 2010-12-24
No, it's not normal. Ubuntu pretty much never freezes on me.

Start by rebooting into recovery mode, or from a live CD/USB key, and running an *fsck* to repair the Linux filesystem.

---

### Post by garvinrick4 on 2010-12-24
If you have a live cd or Usb run it and mount file system.
alt/f2 and in box type gksudo nautilus.
open file system you mounted go to home directory and open
Get the files you want and copy to Windows install or a USB flash, something.
If you want to try and fix system let me know will give you code for live cd. 
Not to hard to run just some copy and paste stuff.

---

### Post by drswingingblades on 2010-12-24
> **noah++ said:**
> No, it's not normal. Ubuntu pretty much never freezes on me.
 
Start by rebooting into recovery mode, or from a live CD/USB key, and running an *fsck* to repair the Linux filesystem.
 
 
can you explain how to use the fsck command? Again, life long windows user, brand new to linux. I Booted off cd and im in the gui, looking for some more guidance
 
 
THANKYOU

---

### Post by drswingingblades on 2010-12-24
> **garvinrick4 said:**
> If you have a live cd or Usb run it and mount file system.
alt/f2 and in box type gksudo nautilus.
open file system you mounted go to home directory and open
Get the files you want and copy to Windows install or a USB flash, something.
If you want to try and fix system let me know will give you code for live cd. 
Not to hard to run just some copy and paste stuff.
 
 
Worked like a charm, when you run gksudo nautilus is it applying the sudo command to everything you do in that window?
 
cause i was trying to "sudo mv /media/Filesystem/Documents" but it wouldnt let me do it.
 
I got the files i needed and i'm going to reinstall Ubuntu anyways cause i installed 64 bit but a friend told me 32 is alot smoother even if you have 64bit components?

---

### Post by garvinrick4 on 2010-12-24
> **drswingingblades said:**
> Worked like a charm, when you run gksudo nautilus is it applying the sudo command to everything you do in that window?
 
cause i was trying to "sudo mv /media/Filesystem/Documents" but it wouldnt let me do it.
 
I got the files i needed and i'm going to reinstall Ubuntu anyways cause i installed 64 bit but a friend told me 32 is alot smoother even if you have 64bit components?
# I just use gksudo which puts me in root in live cd because sometimes you do not have
   permission to move files  and gksudo gives me permissions just in case.
# gksudo is for GUI usually:
```
gksudo gedit /etc/apt/sources.list
```will now let me make changes have opened in gedit editor in root.

---

### Post by garvinrick4 on 2010-12-24
/home/rick/Documents

If you have something mounted in Media:
```
sudo mkdir /media/lucid
``````
sudo mount /dev/sda# /media/lucid
``````
cd /media/lucid/home/rick/Documents
``````
ls -la
```
Now can see docs and permissions in mounted drive in terminal:
```
sudo umount /media/lucid
```

---

### Post by garvinrick4 on 2010-12-24
fsck command is never to be used on a mounted drive it is like chkdsk in Windows.
Ubuntu automatically runs it every 20 or so boots only takes a few seconds to check
filesystem in linux. 
```
sudo e2fsck /dev/sdx
``` 
x being partition number. On unmounted drive (more than one install or live cd)
#I have not run it in quite a while because just have not needed to.

---

### Post by drswingingblades on 2010-12-24
Wow, thats a huge help. Saves me a lot of BS time spent reading forums.

I got all the files moved i needed to and as long as this poop doesnt  happen to me again ill THOROUGHLY enjoy falling deeper into the rabbit  hole of linux. I'm trying to stay away from the GUI and learn more CLI.


But THANK YOU for all the help garvinrick4[URL="http://ubuntuforums.org/member.php?u=899097"]
[/URL]

---

