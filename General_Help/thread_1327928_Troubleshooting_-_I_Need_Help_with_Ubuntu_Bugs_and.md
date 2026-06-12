---
title: "Troubleshooting - I Need Help with Ubuntu Bugs and Difficulties"
date: 2009-11-15
forum: General Help
---

### Post by dylanrallen on 2009-11-15
About a week ago I upgraded to Karmic Koala 9.10 from Ubuntu 9.4.   Ever since the upgrade, my OS doesn't seem like it's operating as well as it was with 9.4.  My internet has extreme lags, can't load videos well (streaming music, videos, steaming usually cuts out).  It's becoming very frustrating, is there a way to fix this? Any other forum threads I could check out to fix the problems?  

Or maybe even directions on to system restore to 3 weeks ago, or even a wipe with using the Ubuntu 9.4 Image Disc I previously to install Ubuntu 9.4.

Please answer back as soon as anyone can.  I really enjoy using the Linux OS, easy to use, but problems like these I can't figure out on my own.:popcorn:

---

### Post by dylanrallen on 2009-11-16
Also, on all my windows, my + and - (maximize, minimize) and my close out x is all gone, nor can I move my windows around anymore..

---

### Post by P4man on 2009-11-16
open a terminal (applications > accessoires) and type

```
uname -a
```

report back what the output is (kernel version). If its 2.6.28.somthing then thats your problem and its solved fairly easily. Try running
```
sudo update-grub2
```

If you have a 2.6.31.sonething kernel then your problem is probably related to the intel videodrivers, and I wont be much help to you.

---

### Post by Giblet5 on 2009-11-16
It sounds like you've got a number of major problems, and I would recommend going back to 9.04. 9.10 does have some quirks, though I have managed to fix them all on my system. So far.

There's no easy way to do go back. You'll have to back up your stuff (I use the tar command) and reinstall.

Here's how I do a backup: I connect a large USB drive that automounts at /media/USBdrive. Then I run this command from a terminal window:
```
sudo tar -cpvzf /media/USBdrive/backup.tar.gz /home
```

After the reinstall, you would restore this via ```
cd /
sudo tar -xpzvf /USBdrive/backup.tar.gz
```

You can also try the following to clean up any user-level misconfiguration of your system. This will log you off and when you log back in, you will have a 'clean slate' configuration (the min/max gadgets should be back too):

```
mkdir dotback
mv .gconf* .gno* .config dotback
sudo /etc/init.d/gdm restart
```

(Note that everything was backed up in case you decide you want it back)

---

### Post by philinux on 2009-11-16
> **dylanrallen said:**
> Also, on all my windows, my + and - (maximize, minimize) and my close out x is all gone, nor can I move my windows around anymore..

Sounds like the whole thing could be related to compiz, turn it off and see.

System>Prefs>appearance>Visual Effects>None.

---

### Post by Giblet5 on 2009-11-16
> **P4man said:**
> open a terminal (applications > accessoires) and type

```
uname -a
```

report back what the output is (kernel version). If its 2.6.28.somthing then thats your problem and its solved fairly easily. Try running
```
sudo update-grub2
```

If you have a 2.6.31.sonething kernel then your problem is probably related to the intel videodrivers, and I wont be much help to you.


P4man was posting to the wrong thread I think.

He's almost certainly correct in that other thread though. He has Mad Perception Skillz, I hear. ;)

---

### Post by P4man on 2009-11-16
> **Giblet5 said:**
> P4man was posting to the wrong thread I think.



Nope.  A lot of people doing an upgrade 9.04 > 9.10 encounter a bug that doesnt update grub and boots the old jaunty kernel, giving all kinds of weirdness. Im not betting money on it but its entirely plausible and easy to find out and remedy.

---

### Post by Giblet5 on 2009-11-16
> **P4man said:**
> Nope.  A lot of people doing an upgrade 9.04 > 9.10 encounter a bug that doesnt update grub and boots the old jaunty kernel, giving all kinds of weirdness. Im not betting money on it but its entirely plausible and easy to find out and remedy.

Ya know, I had that problem upgrading this system. The upgrade did the update-grub, but never did the grub-install.

I spotted it from the grub menu, fixed it and rebooted...

That *would* cause serious mayhem. Nice one, P4man.

---

