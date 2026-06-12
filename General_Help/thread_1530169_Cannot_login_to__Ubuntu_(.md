---
title: "Cannot login to  Ubuntu :("
date: 2010-07-13
forum: General Help
---

### Post by not1 on 2010-07-13
Recently I haven't been able to login to Ubuntu (10.04). This bemused me because I didn't reconfigure anything, didn't mess with xorg or GRUB, didn't remove or install any packages. Nothing.

I am a bit of an amateur end user of Ubuntu (even though I have been using it for years) so hopefully you guys can help me with my symptoms.

It is also worth noting I cannot go into failsafe gnome as a result of not having a splash/boot screen because of a [workaround I had to use to get Ubuntu 10.04 working with my graphics card]("http://ubuntuforums.org/showthread.php?t=1466337").

So yeah I boot up and am met with an older looking GNOME user interface. When I enter my username and password it goes black for a second and the goes back to the login screen.

I also have a caption of the bottom of my screen saying
> INSTALL PROBLEM!
The configuration details for GNOME Power manager have not been installed properly. Please contact your [something something cant remember] administrator
This is perhaps the reason for all my probrems - I have always had something similar relating to GNOME power manager errors coming up occasionally and like any lazy person I ignored them. Probably to my detriment. It may have something to do with the fact that my laptop battery is dead and can only be powered by plug. I have been meaning to replace that thing.

Thanks in advance guys :D

---

### Post by viralmeme on 2010-07-13
> **not1 said:**
> INSTALL PROBLEM!
The configuration details for GNOME Power manager have not been  installed properly. Please contact your [something something cant  remember] administrator

I've seen that error after messing with my configuration. In my case it meant the GUI can't write to /tmp. The solution being to boot from the CD and make /tmp writable by users.

---

### Post by not1 on 2010-07-13
holy moley, I don't even know if my live cd will work considering I originally needed to edit the damn boot line to even get 10.04 working *shakes fist at compuda*

I'll see about your solution if I can find an older disk then. Do you have any *exact* concise instructions on how to go about that for a newbie like me?

---

### Post by mickwombat on 2010-07-13
Have you tried to login as root to test the solution suggested above?

---

### Post by not1 on 2010-07-13
No I haven't tried to login as root.

I'll tell you what I did do though. I logged in SUCCESSFULLY into my user. After what would be about 15 tries over the past week.

I didn't do ANYTHING. The Power Manager error didn't come up.

What the **** is going on? I typed this from my Ubuntu laptop :/

---

### Post by viralmeme on 2010-07-13
> **not1 said:**
> holy moley, I don't even know if my live cd will work considering I originally needed to edit the damn boot line to even get 10.04 working *shakes fist at compuda*

I'll see about your solution if I can find an older disk then. Do you have any *exact* concise instructions on how to go about that for a newbie like me?

<ctrl><alt><F1> will bring up a login screen. Login as user, sudo root, then `ls -la /' and see if /tmp is owned by root:root

If so then `chown root:users', chmod g+rwx ...

---

