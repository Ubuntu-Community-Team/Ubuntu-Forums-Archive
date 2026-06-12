---
title: "Help! I borked the login screen with a custom jpg file - ouch"
date: 2010-12-23
forum: General Help
---

### Post by OGpmpdog on 2010-12-23
Hello,

I used sudo mv and Ubuntu tweak to customize my login screen -end result: a white login screen with a flashing rectangle in the middle - where I click my username.

I cant login, which sux...

Is there a way to use command line (or live CD?) to revert to a regular background jpg file, in home/usr/share/background?

I am using Natty, and hope to sign-in without having to reinstall.

Thanks for reading and Happy Holidays to all.

---

### Post by theasprint on 2010-12-23
Hi,

Yup I suppose it is possible.

I think mount the hard disk which has Ubuntu in it and go and revert back.

Why not give it a try and see what happens?

BTW I'm not sure what is the original, perhaps you would need to get somewhere, or replace with a "confirmed-work" one.

---

### Post by OGpmpdog on 2010-12-23
Thanks for the reply.

I'm dual booting 1 HD:  1)Lynx and 2)Natty for testing.

How do I mount sda3 (Natty) and revert back to original login screen configuration, without erasing everything else?  Also, this would require use of the Live DVD; how would I enable permissions to maneuver sda3 home/usr/share/background folder?

I'm thinking there has to be a way to use the terminal to change the login screen background.

> **theasprint said:**
> Hi,

Yup I suppose it is possible.

I think mount the hard disk which has Ubuntu in it and go and revert back.

Why not give it a try and see what happens?

BTW I'm not sure what is the original, perhaps you would need to get somewhere, or replace with a "confirmed-work" one.

---

### Post by takisan on 2010-12-23
You can log in via command line by clicking <ctrl>+<alt>+<f1> at the login. Then you could see if you could type startx and get Gnome running.

---

### Post by OGpmpdog on 2010-12-23
Thanks for the quick reply!

I have logged into the command line; I tried sudo gdm -restart - and got a funky error message - something like unable to find location.

I will try startx and let you know how it goes.

Peace and Happy Holidays.

> **takisan said:**
> You can log in via command line by clicking <ctrl>+<alt>+<f1> at the login. Then you could see if you could type startx and get Gnome running.

---

