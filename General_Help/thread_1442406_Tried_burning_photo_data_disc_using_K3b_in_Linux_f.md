---
title: "Tried burning photo data disc using K3b in Linux for Windows user.  Didn't work well."
date: 2010-03-29
forum: General Help
---

### Post by ThreeOwls on 2010-03-29
Hello. I just switched over to the Linux OSs Mint and Ubuntu, so I am totally unaware and lacking knowledge in these tech arenas. Looking for some help on this problem.

Okay, I burned a photo data disc for a relative of mine elsewhere in the country last week. Mailed it off and he got it today. He said the disc partially worked. The photo data disc was suppose to have 5000 plus photos on it, but he said only 3000 photos showed up and that a few hundred of the 3000 were scrambled in picture quality. 

For the photo data CD I sent him, I used this:

OS: Linux Mint (basically a derivate of Ubuntu OS)
CD Burning App: K3B
Speed Of Burn: 16x 
Type Of Disc: Sony CD-R
File System: "Linux/Unix + Windows"
Volume Name: "Family Photos"

Also, I don't know if this would cause a problem, but my hard drive is partitioned into many drives. The two separate Linux OSs (Mint and Ubuntu) have their own 20GB partitions which are in Ext4 system, while all my other data and photos and MP3s are on separate partitions which are in NTFS system. Could that screw things up? Do the data, MP3s, and photos need to be in Ext4 or Ext3 systems to get good data disc burns or any other type of disc burns while running K3B in a Linux OS using Ext4???

Did I do something wrong? Did I use the wrong file system? I know 16x is a low and good speed to burn at and lessens the chances of bad burns in Windows. What happened? I used Nero 7 a lot in Windows and never had these issues in the past. What is the problem? And how can I fix it? Is K3B not a good data disc maker?

Or is it Linux burned CDs have trouble with certain Windows CD/DVD optical drives?

I really don't want to go back to Windows, but if I can't figure out how to burn "data discs" for my relatives to send to, I will be forced to. I really want to stay and learn and use Linux well enough. PLEASE HELP!!!

---

### Post by foxmulder881 on 2010-03-29
Having multiple partitions is not the problem. And neither is having ntfs in use. It's more than likely just a dodgy burn or dodgy disc you burnt to. Did it work when you tried it after you burnt it on your own PC? Oh and also in K3b, did you make sure Windows Compatibility was enabled?

---

### Post by ThreeOwls on 2010-03-29
> **foxmulder881 said:**
> Having multiple partitions is not the problem. And neither is having ntfs in use. It's more than likely just a dodgy burn or dodgy disc you burnt to. Did it work when you tried it after you burnt it on your own PC? 

thank you for replying first off.

okay, when i burned the photo data cd i did a quick look.  basically, i put it back in the disc drive to see if the OS saw it. It did, it showed the disc having the name "Family Photos".  I also went and did a quick look at the disc and saw photos and folders as expected when using the file browser that comes with Linux Mint.


Post Script Question, is there a good CD-R disc name-brand to use with Linux OS burning apps or is it like Windows in general.  I usually get brands like Sony, TDK, Verbatim, and HP LightScribe discs.

> Oh and also in K3b, did you make sure Windows Compatibility was enabled?

okay, i might not be understanding you here or might be talking about something else.  Are you asking me did I have the K3b file system burn setting set to "Linux/Unix + Windows" ?? If so, yes, I had that chosen.  Or are you asking something else?   Is there something I didn't have installed or checked on in the Linux OS or in the K3b application?  If it is the latter, please tell me how this effects things and, of course, how to put it right

---

### Post by foxmulder881 on 2010-03-30
> **ThreeOwls said:**
> is there a good CD-R disc name-brand to use with Linux OS burning apps or is it like Windows in general.  I usually get brands like Sony, TDK, Verbatim, and HP LightScribe discs.

If you stick to any reputable brand name, you shouldn't have any dramas. Avoid cheap nasty media. Much the same as you would on Windows.

> Are you asking me did I have the K3b file system burn setting set to "Linux/Unix + Windows" ?? If so, yes, I had that chosen.

Yes, that's what I was asking.

---

