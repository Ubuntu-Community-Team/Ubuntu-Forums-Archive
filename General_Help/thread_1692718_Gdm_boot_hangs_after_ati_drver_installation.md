---
title: "Gdm/ boot hangs after ati drver installation"
date: 2011-02-21
forum: General Help
---

### Post by Itmth19 on 2011-02-21
I have just installed a fresh ubuntu 10.10 and i want to install catalyst ati driver on ubuntu.
I have tried installing a 11-2 driver version before, but it hanged on the first boot.
Then i decided to have a fresh ubuntu installation, and then get the propriate driver that automatically download and install by driver applet. But the hang repeat..

However, when i trying to fix this stuck, i access the recovery mode>prompt from root, and then i type STARTX, and everythings worked beautifully, fglrxinfo works fine.  But if i got SERVICE GDM START, it hanged again.

I have searched many threads about this problem, i have tried "dpkg-reconfigure xserver-xorg", which seemed to work perfectly with many cases, but not mine.

I don't know where i got wrong, please help me.
I am real nob and need some help. Thx all.

---

### Post by gordintoronto on 2011-02-21
dpkg-reconfigure xserver-xorg
is incorrect. Try:
dpkg -reconfigure xserver-xorg
with a space after "dpkg".

Did you run System/Administration/Additional Drivers to get the ATI driver?

---

### Post by Itmth19 on 2011-02-22
Thank you so much, i'm gona try it later. I install by the driver applet as in your question. What 's my problem out there?

---

### Post by Itmth19 on 2011-02-22
i've tried dpkg -reconfigure but it seems there is no -reconfigure option for dpkg. i've tried dpkg-reconfigure xserver-xorg but nothing happened. anyone has ideas?

---

### Post by Itmth19 on 2011-02-22
bump

---

### Post by tanpopo_chan on 2011-03-17
I had a similar problem and this is how I solved it...

[http://ubuntuforums.org/showpost.php?p=10568075&postcount=2](http://ubuntuforums.org/showpost.php?p=10568075&postcount=2)

---

### Post by lithopsian on 2011-03-17
When X fails to start, or starts but you can't see anything, look in the log (/var/log/Xorg.0.log).  X very conveniently keeps a copy of the log from the previous attempt to start so you can look at it after you're rebooted to something that works.  Look in it and you will (probably) see an error or ten.  Then you will know what the problem is, or at least be able to show us what the problem is.  Someone here might even be able to tell you how to fix it, rather than just flailing about running fixes that someone else found for a different problem.

---

