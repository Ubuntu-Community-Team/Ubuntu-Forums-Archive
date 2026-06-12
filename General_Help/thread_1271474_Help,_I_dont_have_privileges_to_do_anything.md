---
title: "Help, I dont have privileges to do anything"
date: 2009-09-20
forum: General Help
---

### Post by JKoczeniak on 2009-09-20
I am using Ubuntu 9.04 and I had everything working great then I was playing around with the Users and Groups tab and by accident I removed my self from everything so now I cant add myself back into the groups because it says that I dont have rights.  I have looked around on the web for a little bit and I only found one person who did this in Ubuntu Server which doesnt have a Gui.  I tried to open the terminal and type:

sudo passwd root
then entered the root password and got
jasonk is not in the sudoers file

How can I add myself back to the correct groups or atleast get access to Users and Groups again and I can add it from there.  I know the sudo or root password.

I am a newbie so I apologize about the incorrect terms and what not.
Thanks.

---

### Post by Whiffle on 2009-09-20
Should be able to fix it by rebooting into recovery mode at the boot menu, then select "root" at the Recovery Menu, then run:

```
usermod -a -G admin <yourusername>
```

then do

```
shutdown -r now
```

to restart, and you should be good to go.

---

### Post by JKoczeniak on 2009-09-20
Thanks, I am going to try that now

---

### Post by JKoczeniak on 2009-09-20
That worked, thanks a lot.

---

### Post by Whiffle on 2009-09-20
No problem :)

---

