---
title: "Can't boot into Jaunty"
date: 2009-08-17
forum: General Help
---

### Post by painterboy on 2009-08-17
Hey I was hoping someone could help me with this. I installed 9.04 64 bit version last night on my laptop dual booting Vista. The install went fine and I got some things up and running downloaded some stuff via synaptic then my laptop froze which had never happened to me using Linux before. I restarted my computer and selected the ubuntu install from grub. It started to boot up again then hangs and gives me the busy box error I've attached below. From what I have seen there seems to be a bug that has been reported about trouble booting Jaunty but the error given in the report is not the same as mine at least so far as I can tell. 
If anyone has any ideas please let me know.

Thanks in advance

---

### Post by j7%&lt;RmUg on 2009-08-18
I dont think i can be much help with this but i had a similar error about 3 weeks ago.

I had this appear at boot and it got to the "no resume image trying normal boot" part, then it booted into ubuntu. It started appearing after i martially stuffed my system up by trying to swap my GFX cards around, i have no idea what caused it.

Sorry i cant be of more help but i will check this thread later to see what other people say.

---

### Post by HiImTye on 2009-08-18
I had this issue when I first installed Ubuntu ages ago. I was using the 'install with windows' or whatever option on the CD. I gave up on Ubuntu until I got annoyed with XP again and just started over. got sick of microsoft BS (wanting me to enter my freaking reg code to use the repair tool which didn't actually fix anything). and installed Ubuntu fully. never looked back.

---

### Post by bchurchill on 2009-08-18
Given that it looks like it can't find certain files, I'd try booting from a live CD, mounting your HDD and checking to see if those files exist, ESPECIALLY /sbin/init.  If /sbin/init doesn't exist, your system won't work.   If several files don't exist you'll need to either (1) Reinstall Ubuntu (easy) or (2) restore all the missing files, find any changes, do a bunch of config...  My guess is that windows overrode some critical pieces of your Ubuntu partition.  (Annoying, I know)

Which set of instructions did you follow to do the dual-boot?  The community wiki has some good ones if the ones you used were shakey.

---

### Post by painterboy on 2009-08-18
I've had time to look around which has lead me to this post

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all")

apparently it is kernel 2.6.28-11 that ships with jaunty which is causing massive file corruption on some 64 bit systems. The recommended action is to replace the kernel with 2.6.29 and jaunty should be stable again.

For me I'm just going to try a fresh install of Karmic Koala instead. 
Wish me luck.

---

