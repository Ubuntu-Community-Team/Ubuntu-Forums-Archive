---
title: "Mount of filesystem failed..."
date: 2009-12-28
forum: General Help
---

### Post by Zoyberk on 2009-12-28
Last few days every time i reboot my Ubuntu 9.10 laptop i gat this
```
Mount of filesystem failed. a8d932-6c28-4c09-8b0e-23a20e8c5a9d
A maintenance shell will now be started.
CONTROL-D will terminate this shell and retry.
root@server-desktop:"#
```

running fsck fix it but it takes about 10-15 min to do it, well problem is that i need to run that like every time i reboot computer...
And while on ubuntu, turned on it happened few times that i start getting Error: read only fliesystem
So i cant move files on my disk, i cant download, i cant delete itd...

Dunno if that is cause of problems bust most of time i play Kotor on wine, surf web whit chromium, and dowload whit transmission...

Would really apriciate if somebody could help, cuz thats making my ubuntu quite unusable...:)

---

### Post by JamesWeng on 2010-01-12
Input the command 'fsck', this command will help you to fix all logic issue on your HD.
And then 'reboot'.

James

---

### Post by Mr Nemo on 2010-01-12
This happened to me about a week ago, running that command seemed to fix everything, but i could never figure out why that happened in the first place. Any reason it happened to you?

---

### Post by YetAnother on 2010-01-12
Your file-system is getting corrupted. It could be anything from power failure/improper shutdown/hardware error/driver/filesystem/kernel bug.
Taking a look at /var/log/dmesg,kern,messages might give you a hint.
Try shutdown(not suspend/hibernate) and restart and see if it gives you the error.

---

### Post by mixtri on 2010-01-13
I just got the same exact error message, only that after running FSCK Ubuntu does a check then returns the same error message after reaching 50%. This is the third time in a year this has happened to me. The last time I lost everything including the hard disk which was rendered useless, I now have a 1TB h/disk and will absolutely go NUTS if I loose my data again. It's extremely annoying this happens as I have no idea of what may have caused. I shut down correctly last time I used the blasted thing. Any help will be much appreciated. thanks

---

### Post by NFblaze on 2010-01-13
Try doing *fsck*. Then try *mountall* after that. It worked for me yesterday, when my computer would not boot to completion numerous times.

---

### Post by mixtri on 2010-01-13
Okay I'll give that a go. Thanks NFBlaze. Do I type in the mountall command after fsck fails and returns to root@ubuntu?

---

### Post by NFblaze on 2010-01-13
Yes. Try after you try to fsck and it fails. I'm not guaranteeing it will work I'm just saying that is what worked for me day before yesterday.

---

### Post by mixtri on 2010-01-13
Thats great dude, its working now after several fixes. Weird how so many files, inodes etc get corrupted or missing. Thanks a lot.

---

### Post by KeiththeMusic on 2010-01-13
This happened to me just now and I ran fsck and mountall one right after the other and it worked great.  Thanks fellas....

---

### Post by escaleraroyal on 2010-01-15
i got the same error but when i type in fsck, it won't work. it says /bin/sh : fsck: not found
any help would be appreciated.

---

### Post by evanston4393 on 2010-01-15
Im having a very similar problem, however mine doesnt even make it into a terminal, its a slimmed down version with very few possible commands to run. When i boot into the LiveCD and run fsck it appears taht it doesnt do anything, it jsut says something like "fsck from utils.ng soemthing something something" and it still fails to boot. Any ideas?

---

### Post by ThePantryMaster on 2010-01-15
My laptop has no working battery, so when it's switched off, the bios time and date isn't correct.  If I try and boot it without setting the time and date the file system fails to mount.  Could be something as simple as your time and date in the bios?

---

### Post by evanston4393 on 2010-01-15
> **ThePantryMaster said:**
> My laptop has no working battery, so when it's switched off, the bios time and date isn't correct.  If I try and boot it without setting the time and date the file system fails to mount.  Could be something as simple as your time and date in the bios?
Possibly for him but not for me, i have windows also on my machine which im forced to use at the moment and it is keeping time perfectly fine.

---

### Post by NFblaze on 2010-01-15
> **escaleraroyal said:**
> i got the same error but when i type in fsck, it won't work. it says /bin/sh : fsck: not found
any help would be appreciated.

I dont know but it sounds like it could be busybox or maybe the grub bash-like shell.

See if you can cd /sbin and then try fsck from there.

---

### Post by GeorgGoodchild on 2010-03-07
"Fsck" worked for me too, Thanks fellas I was about to reinstal the OS. :p

---

### Post by joepz on 2010-04-16
Mmmm,
Problem keeps coming back for me. I used the 'fsck' command a couple of times and things/inodes etc. seem to be fixed.
 
However still, during a session it seems the drive is lost/dismounted at some point. Programs won't start anymore and files cannot be read. Running Ubuntu from live CD give me all required access & functionality but in normal mode it is not stable.
 
Restarting using the 'fsck' command does help for a while, but problem comes back and seems to be something is structurally wrong.
 
I did a full memory test, no problem. Lately I added a 256MB ATI PCI videocard. Could this make it unstable? Removing it does not solve the problems. 
 
Any suggestions?
I think I go for a fresh install 10.4 when available!
Good luck to you all

---

### Post by davegod on 2010-06-06
> **ThePantryMaster said:**
> My laptop has no working battery, so when it's switched off, the bios time and date isn't correct.  If I try and boot it without setting the time and date the file system fails to mount.  Could be something as simple as your time and date in the bios?
This just worked for me.

---

### Post by peterqb on 2011-12-23
> **JamesWeng said:**
> Input the command 'fsck', this command will help you to fix all logic issue on your HD.
And then 'reboot'.

James


Thanks very much, James. This has fixed it for me too. Much appreciated.

Peter

---

### Post by oldos2er on 2011-12-23
Closed, necromancy.

---

