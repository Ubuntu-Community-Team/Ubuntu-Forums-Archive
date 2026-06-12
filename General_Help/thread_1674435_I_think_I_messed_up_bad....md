---
title: "I think I messed up bad..."
date: 2011-01-23
forum: General Help
---

### Post by u-noob-tu on 2011-01-23
I'm not even sure where to start... I had been looking for what I thought was my primary graphics when it turned out I had an intel chip. So I ended up at [http://intellinuxgraphics.org/install.html]("http://intellinuxgraphics.org/install.html"), and found the instructions for the 2010q4 drivers. Unfortunately it had to be compiled from many different sources, but I felt confident enough to do it. I managed to get all but one done (the last one), when I thought it would be a good idea to reboot. Well, when I gdm now I just see a flickering small white box, but I can hear the user profile selector sound. I can't type anything in. Slightly panicking, I rebooted into recovery mode and managed to remove the intel driver but not the Mesa one, and it's that one that is the issue I think. Then I inserted a live I wisely kept. Well, it is not working as of this writing. It gets to the try ubuntu window and hangs. I am kinda freaking out. If I wrecked my laptop my dad will disown me (technically it's his laptop). I am willing to do a clean install. I don't have anything important on my laptop. PLEASE RESPOND QUICKLY!!!

---

### Post by sum1nil on 2011-01-23
You may want to try puppy linux: [http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

to access your ubuntu partition. I believe it has the ability to r/w files on the linux partition.

There is a way to avoid grub2 just do a search on the forums. You'll be booting into text mode and there is a little box with the option to 'recover'. I'd try that first.

Here is how I avoid grub2 (if needed):
From Puppy (hope it reads/writes), browse to /boot/grub/grub.cfg
on the line 'set default=0' change that to 3, save, and then reboot.
Hopefully, you'll get that box that has a recovery option. You can also continue booting and do a 'grub-update' after logging in.

Hope it works for you.

---

### Post by u-noob-tu on 2011-01-23
thanks, but i managed to get the live cd to run a reinstall. i really dodged a bullet there. i kinda needed to do a reinstall, i had a lot of junk on my hard drive anyway. :p

---

### Post by Vaphell on 2011-01-23
did you create a separate /home partition? Separate /home saves you a lot of trouble with recovery when system is hosed beyond the ability to repair it. If something fails you simply reinstall the core of the system while user files and configuration are there untouched.

---

### Post by u-noob-tu on 2011-01-23
> **Vaphell said:**
> did you create a separate /home partition? Separate /home saves you a lot of trouble with recovery when system is hosed beyond the ability to repair it. If something fails you simply reinstall the core of the system while user files and configuration are there untouched.

nah, i didnt even know i could do that. im still fairly new at this. no serious harm done though.

---

