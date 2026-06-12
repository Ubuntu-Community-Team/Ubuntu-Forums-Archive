---
title: "Please help me! I'm locked out of my own computer!"
date: 2009-09-17
forum: General Help
---

### Post by PrinceK on 2009-09-17
Well, I'm not really locked out, but I got this laptop from my brother, and when he gave it to me, he just deleted his account, and made mine. But he didn't give me admin powers, so I have no admin privileges, but none of the accounts do, so I can't change this.

Would I have to reinstall Ubuntu?:(

If you dont get what I just said:

I don't have admin privileges, but I can't change that I don't have them, because there is no admin account.

---

### Post by Whiffle on 2009-09-17
Should be able to fix it by booting it into recovery mode at the boot menu, then select "root" at the Recovery Menu, then run:

usermod -a -G admin <yourusername>

---

### Post by PrinceK on 2009-09-17
Thank you so much Whiffle, I'll see if this works!

---

### Post by Whiffle on 2009-09-17
oh and its 

shutdown -r now 


to reboot :)

---

### Post by jerrrys on 2009-09-17
if that doesn't work

[http://ubuntuforums.org/showthread.php?t=1146638&highlight=password](http://ubuntuforums.org/showthread.php?t=1146638&highlight=password)

---

