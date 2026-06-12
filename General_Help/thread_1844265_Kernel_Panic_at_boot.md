---
title: "Kernel Panic at boot"
date: 2011-09-14
forum: General Help
---

### Post by rhapa on 2011-09-14
Hello guys,

I having some issues in my installation lately (some crashes and a little bit slowing down) but today it got worse. While booting the system just panic and comes up with a error message saying that was impossible to mount root directory. Here I attached pictures of the screen with the error, on while normal booting and one while trying to boot in recovery mode (which comes up with the same error). Usually I would just save my important data and would reinstall the system but actually I have some downloads occurring in this installation that I really can not lose (specially one of 8.4 gb that has already downloaded 47%, :().

Does anyone have a clue on how to fix this? Thank You....

My system specs:

Ubuntu 10.10 32bit (if it's useful it has all japanese package installed running with iBus)
cpu: AMD X2 5000+ 64bit
gpu: Nvidia GeForce 8600GT 1gb
ram: 2gb kingston
hd: 320gb samsung sata
drive: dvd-rw lg

---

### Post by rhapa on 2011-09-15
I did what this person did to boot his system but unfortunately my system didn't boot. Well, I ran Nautilus as root and deleted all files linked to the kernel, to see if the system would load the kernel automatically but it didn't happen. The system shows up an error that I need to load the kernel first and that some files were missing. Now I installed Ubuntu 10.10 alongside this cracked installation so I'll see if copying the files from the other OS will work on this. Hope I'm successful.

---

### Post by rhapa on 2011-09-15
Well, I just fixed the problem:guitar:.
The only thing I need to do was to re-install grub to the mbr. As soon as I couldn't get it installed manually (actually I don't know how) I just installed a clean installation alongside the one I wanted to fix. Then I copied the files from the /boot directory (from the new install) to the /boot directory on the broken system and then I just put the entry to its partition in the currently grub.cfg.

Actually it was as easy as taking a child's candy. Just logic. From now on I'm gonna manage on how to install grub manually.

---

