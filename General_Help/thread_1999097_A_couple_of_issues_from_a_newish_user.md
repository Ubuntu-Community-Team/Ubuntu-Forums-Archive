---
title: "A couple of issues from a newish user"
date: 2012-06-07
forum: General Help
---

### Post by Quail2 on 2012-06-07
The first problem I'm having is the backlight issue. Booting up turns off the backlight, so I can only boot up in recovery mode. I've tried a couple of things to fix this, but they haven't worked.

The second problem is that when I log in on my account, it's in low graphics mode (I think) and I can't use the terminal. It won't let me type in the terminal. It's just black and there's no cursor. When I log in as a guest, the graphics are normal.

I need to be able to use the terminal to fix the backlight problem and I don't quite understand why it's booting up in this low graphics mode.

---

### Post by LiamOS on 2012-06-07
Is this after a new install or is this a new issue?

If you know how to correct the backlight issue from the terminal, you could boot up a live CD/USB, mount your root partition and then edit the files from there. Ubuntu's live media will do just fine, but you can use almost any live media.
Just in case you're not entirely sure how to go about this, it would be something like:
```
# mkdir /mnt/ubuntu
# mount /dev/sda[appropriate partition number here] /mnt/ubuntu 
----{Assuming you have /usr, /sys and /etc on the same partition as / }
# cd /mnt/ubuntu 

```
You can now edit the appropriate files, as they'll be in /mnt/ubuntu/sys or /mnt/ubuntu/etc or such.
If you want to do quite a lot of work in there while you can, it might be easiest to chroot into the environment, so you can use APT and such to correct your system if necessary:
```
# chroot /mnt/ubuntu /bin/bash 
```

---

