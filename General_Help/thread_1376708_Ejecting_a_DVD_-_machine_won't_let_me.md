---
title: "Ejecting a DVD - machine won't let me"
date: 2010-01-09
forum: General Help
---

### Post by zcacogp on 2010-01-09
Chaps, 

I am trying to play a DVD across a network. It isn't going that smoothly, but that's the topic of another thread on here ... 

However, I am having difficulty ejecting the DVD from the machine it is placed in, once it has been accessed across the network. 

Sequence goes like this: 

I place a DVD into the DVD drive of my desktop machine. It works fine. I watch it, stop it, eject it. All is well. 

I place a DVD in the DVD drive of the desktop machine, and then open it on one of the two laptops I have. It appears to open OK. I close it, and unmount it from the laptop. It unmounts OK (using "sudo umount /media/cdrom0")

I then try to eject it from the desktop machine. It doesn't work. 

1. I right-click on it on the desktop, and click "Eject". I am told "Unable to eject DVDVolume. Failed to eject medium; one or more volumes on the medium are busy.". 

2. I try "eject" (or "sudo umount /media/cdrom0"). I am told that "umount: /media/cdrom0: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
eject: unmount of `/media/cdrom0' failed"

3. I try "lsof /media/cdrom0" and get nothing (the command prompt comes back.) Same if I try "fuser /media/cdrom0". And, after doing either (or both) of them I still can't open the DVD drive. (I don't know whether these commands are making any sense - I am guessing a lot.) 

The only way to get the DVD back is to re-start the machine, and press the "eject"  button on the device during the boot-up sequence. Surely there must be a better solution than this? 

The volume is being mounted on the lappies using NFS, and I can post my /etc/exports and /etc/fstab files here if need be. Both the lappies and the desktop are running 9.10 Karmic. 

Thanks, in advance, for any help. 


Oli.

---

### Post by scouser73 on 2010-01-09
Rather than restarting the desktop PC in order to unmount the DVD there should be a small hole on the front of the DVD drive where you can insert a paper clip, and this in-turn releases the DVD drawer.

---

### Post by zcacogp on 2010-01-09
scouser, 

Erm, yes ... I haven't tried it but there is such a hole, and I think it does work as you say. 

But isn't that a bit of an inelegant, 'brute-force' type solution? There must be a better way, surely? 

Thanks for your help. 


Oli.

---

### Post by rnerwein on 2010-01-09
hi 
see the man pages on your system for "eject". i think there are the options you need to solve your problem (may be -i )
ciao

---

### Post by zcacogp on 2010-01-09
rnerwein, 

Thanks ... no game (as far as I could see). 

-i was interesting, but served to disable or enable the eject button on the front of the DVD player itself. It didn't then allow you to force eject the disk. 

Thanks for your help tho'. 

Anyone have any other ideas? 


Oli.

---

### Post by zcacogp on 2010-01-11
rnerwein, 

I owe you an apology sir; you were right, the option to force eject a disk (although I'm not quite sure why it is necessary) is -l (lower-case 'L'). 

So the command is: 

# sudo umount -l /media/cdrom0

(or wherever your drive is mounted.) 

Thanks for your help. Sorry I was so dismissive. 


Oli.

---

