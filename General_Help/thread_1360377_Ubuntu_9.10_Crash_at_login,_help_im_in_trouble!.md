---
title: "Ubuntu 9.10 Crash at login, help im in trouble!"
date: 2009-12-20
forum: General Help
---

### Post by Struki on 2009-12-20
It's 3 am and after a fresh install of koala and an hour and a half setup and costumization I get a black screen with no error, acces to terminal, no nothing I had to reboot my laptop, and the horror... Ubuntu wont start i pass the grub and see the ubuntu loading bar hear the sounds and then it freezes and i get the black screen again have to reboot. I'm new with linux so i don't know what to do on recovery mode...

Someone pls help cause i need my computer in the morning and  I use ubuntu as primary OS. What do you need to know? anyone!!??.

---

### Post by Struki on 2009-12-20
Ok weird now i tried again and for no apparent reason ubuntu boot up normally aftter lie 10th attempt , but i got a feeling it could go out any second. Is there a way to run a system check or something and see what's wrong?

---

### Post by john newbuntu on 2009-12-20
First make sure you have all the updates using update manager (System->admin->update manager).  Next check your logs to see if you can spot anything.  The logs are located in /var/log directory and you probably need to look at a few files that start with dmesg, syslog, kern, Xorg etc.  Most of these have time and date.  Look up the logs when your boot failed.

---

### Post by Struki on 2010-02-11
Hey I'm really sory i missed your reply.  Anyway I opened /var/log and I got a lot of those files, cause this crashes happen often. I posted another thread with some more details: [http://ubuntuforums.org/showthread.php?t=1402806](http://ubuntuforums.org/showthread.php?t=1402806)
So you can check it out.
Ok so what am i looking for in the log folder?

---

### Post by Richard1979 on 2010-02-11
It's probably your video drivers.
Check that your have the Proprietary drivers installed (System > Admin > Hardware Drivers).
If you DO have them, then try removing. If you do NOT, then try adding them.
Then reboot and try again.

If the above doesn't work, uninstall compiz and try the steps above again. (sudo apt-get remove compiz)

---

