---
title: "password help"
date: 2010-04-16
forum: General Help
---

### Post by hussainmb on 2010-04-16
Hi,

I'm pretty new to linux. I bought a ubuntu laptop sometime ago
(8.04 hardy, gnome 2.22.3, kernel linux 2.6.24-24-lpia)

i created a username back then, but i am not sure if i gave a password (if i did i don't remember it now).

I can login into the system fine (no password required), however when i try to install/uninstall S/W it asks me for my user password. 
I tried resetting the password using the ESC at reboot, but nothing happens, my system just boots normally although i'm pressing/holding the ESC key.

is there any way i can rest the password using kernel ?? 
or
how do i enter the GRUB mode, i dont seem to be getting into it..

please help...

---

### Post by spiky001 on 2010-04-16
I know this is not the answer but as you have an old OS 8.04 why not upgrade to 9.10 or wait till 10.04 then sort the password out then, or is there a reason you need heron?

---

### Post by darolu on 2010-04-16
Try with Ctrl+C when GRUB loading screen shows up; that should give you access to shell.

From there, you should be able to change the password with:
```
$ passwd <username>
```

---

### Post by hussainmb on 2010-04-16
i didnt upgrade mainly because my comp specs aren't very great (1 GD memory, intel atom cpu N270 1.6GHz, and 0.5GB free space on HD)

i fear an upgrade will need more than what i have, and besides i only use the laptop for browsing and watching movies, this version seems fine for it.

---

### Post by coffeecat on 2010-04-16
> **hussainmb said:**
> I bought a ubuntu laptop sometime ago

Is that a Dell laptop by any chance? Because it seems that they set a timeout of zero in the grub menu so that pressing escape to get the grub menu has no effect. Which strikes me as being absurd, since people in your situation need the grub menu to get into recovery mode to reset the password.

Anyway, if yours is indeed a Dell, have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1163371](http://ubuntuforums.org/showthread.php?t=1163371)

Ignore my posts - I was no help at all. Go to post #7 where aysiu joins in. That thread was for a netbook which doesn't have an optical drive - hence the complication about having to make a bootable USB stick. If yours is a laptop with a CD drive, you should be able to use a live CD and follow aysiu's method for editing the shadow file (post #12).

Good luck!

---

### Post by hussainmb on 2010-04-17
Yes it is a Dell

and thanks a lot... those posts helped.

i was able to reset it.

thanks.

---

