---
title: "Partitioning and installing"
date: 2011-01-22
forum: General Help
---

### Post by jls23 on 2011-01-22
Currently I have Windows 7 and Fedora 13 on my laptop. I'd like to do two things now. First I'd like to give Windows more space, and second I'd like to replace Fedora with Ubuntu. I was worried about deleting the Fedora partition in Windows because my computer wants to boot up in Fedora in default and I didn't know how that would affect it, or if I'd even be able to boot up Windows afterwards.

---

### Post by tredegar on 2011-01-22
Boot to fedora.
Use **fdisk -l** and **mount** to determine which are your linux partitions. Make a note of these, and where your windows partitions are.

Boot the ubuntu CD
Choose "Try unbuntu", so it _does not install_.

Run **gparted** to resize your windows partition (may take some time).
Again, make a note of which partitions are which.

Reboot to windows, make sure it still works (you did backup your personal files [from both win and linux] I hope).

Reboot with the ubuntu CD
This time choose Install
Choose "Manual Partitioning".
Use the data you collected earlier to help you make the right choices: let ubuntu use the old fedora swap partition as swap, let ubuntu use the old fedora / partition as ubuntu's /. Same for /home partition (if you had one).
No need to uninstall fedora, it'll just be overwritten.

Let ubuntu install grub to the MBR, the win install will be detected (I read that  sometimes a win recovery partition is listed as the OS partition and *vice versa*. If this happens, you'll notice and can abort and try again).

That's about it.

---

### Post by jls23 on 2011-01-22
Okay, I did get my partitions resized and started to install Ubuntu. I got to the screen where I was setting up a password and could not continue. The button never activated and I waited until the point where it said "waiting on you." I may have a bad disk and need to retry. At this point it won't boot up Windows either. Currently I put my Fedora CD in and am running it live. I'm thinking I may have to try reinstalling it, but now that I got my partitions resized it shouldn't be a problem replacing later.

---

