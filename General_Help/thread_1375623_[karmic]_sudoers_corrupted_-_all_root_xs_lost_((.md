---
title: "[karmic] sudoers corrupted - all root xs lost :(("
date: 2010-01-08
forum: General Help
---

### Post by rene197705 on 2010-01-08
Ok, i made a mistake by entering a faulty line into /etc/sudoers
And before that another one by forgetting my root passwd


 However, i did not expect sudo to stop working completely when it has 1 bad line in /etc/sudoers
 I also did not expect that every tutorial on how to reset your root passwd just doesn't work for me.


 Rebooting into recovery mode gets me a root prompt that is unable to use passwd.
Something about failure to update the token, file-system read-only.
But mount reports that it's in rw. strange.


 Holding shift while selecting recovery mode in grub (which is a STUPID way to get to an extra menu btw) gets me a menu that i'm unable to navigate with the cursor keys. After a few seconds, it nags about not being able to mount file-systems, then continues booting to a login-prompt, which is of course useless to me at this moment.
 

FFS, go fix this huge bug, starting at /etc/sudoers.
 

rene@ekster:~$ uname -a
Linux ekster 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux


reported also in [https://bugs.launchpad.net/ubuntu/+bug/504671](https://bugs.launchpad.net/ubuntu/+bug/504671)


help with this would be much appreciated.

---

### Post by rene197705 on 2010-01-08
Ok, i was able to solve the problem like so:

- boot off ubuntu karmic live CD 
- goto Applications | Accessoires | Terminal
- enter these commands:
sudo fdisk -l
  (then note which /dev/xxxx entry is your now-faulty root filesystem)

sudo mkdir /media/x
sudo mount /dev/xxxx /media/x
sudo apt-get install vim
sudo vim /media/x/sudoers

Still, the original report stands. It could've been a lot easier to solve if sudo isn't quite so paranoid.

---

