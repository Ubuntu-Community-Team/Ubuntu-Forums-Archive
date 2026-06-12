---
title: "Configuring first boot OS"
date: 2010-01-28
forum: General Help
---

### Post by zozie on 2010-01-28
Hi all;

I installed Ubuntu a few months ago on my Dell inspiron 1318.
All works really well, however my only only problem with the setup is the boot selection screen.
Is there a way to put Vindoz in the first spot instead of Ubuntu?
I use them about 50-50 of the time but would still prefer windows as default because my wife uses that with her accounting software and she goes nuts when she turns it on and it goes to Linux.
thanx:p

---

### Post by spiderbatdad on 2010-01-28
I'm guessing at this based on old ways when the file system was a little different, but it looks like...If you look at the file /boot/grub/grub.cfg and count the number of "menuentry" You will see a boot option in each, and you have, say 6, with Windows as the sixth...then consider the first entry zero...so windows is actually 5.

Now go as root and edit the file /etc/default/grub
Near the top where it says "GRUB DEFAULT=0" Change that to 5
...in this example. Your number may be different. Notice in the comments of the file Run sudo update-grub after editing and saving the file. Good Luck.

---

### Post by zozie on 2010-01-28
Kewl I'll try that. 
thanx

---

### Post by spiderbatdad on 2010-01-28
You might also look at startup-manger in synaptic package manager. According to community docs it works with grub2 and is a gui tool. I believe it installs to System>>Administration...or Accessories.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

