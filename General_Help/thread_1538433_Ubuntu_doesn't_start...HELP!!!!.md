---
title: "Ubuntu doesn't start...HELP!!!!"
date: 2010-07-25
forum: General Help
---

### Post by pumax on 2010-07-25
Hi all,
after several months I have been using ubuntu 10.04 yestarday it didn't start anymore. 
It stucks after ubuntu purple screen (that one that has small ball that indicate loading) by showing black screen.
I haven't update or changed video card driver before.
If i press alt+f1 I can't see any error.

I tried (from recovery mode) without result:
1.fsck on the partitions
2.aticonfig --initial (i have an ati video card)
3.apt-get install ubuntu-desktop
4 dpgk-reconfigure -a

Thanks!!

---

### Post by quixote on 2010-07-27
I'm not sure I understand: is this the first time you used your ubuntu install after several months?  Or have you been using it for several months, and then suddenly this happened?

I'm also not sure from your description: do you get the login screen, and then after you log in, you just get the black screen?  Or does this happen just before the login screen?

If you boot with a livecd, can you see your usual hard drive?  If yes, it might be a good idea to move any data files you want, or your whole /home/your-user directory, from /home/your-user to a usb thumbdrive or the like.  If things go very pear-shaped, then at least you'll have your data!

---

