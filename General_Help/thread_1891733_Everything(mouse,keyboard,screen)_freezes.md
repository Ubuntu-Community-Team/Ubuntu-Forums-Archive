---
title: "Everything(mouse,keyboard,screen) freezes"
date: 2011-12-06
forum: General Help
---

### Post by ioan1ioan on 2011-12-06
Hi everyone,
i installed ubuntu (11.10) using wubi(download wubi and run it) through my win 7 proffesional. Everything during installation went ok, except from the end where the login screen appears and demands the password in order to login. Then after 10 at most seconds everything freezes and after some minutes computer shuts down. I tried to uninstall and re-install ubuntu several times but still the problem exists. Does someone knows what should i do? I am quite starter in using ubuntu so i would appreciate it if the instructions will be detailed.
Thanks.

PS: In that desktop i used to have windows xp / ubuntu 10.04 dual booting without any problem. Also the fan in graphic card is broken so i replace it with a universal one.

---

### Post by BC59 on 2011-12-06
Looks like your hardware is not fully compatible and Wubi has problems booting (ACPI) and you deal with video problems. 

Check here to do some workarounds:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by didinium on 2011-12-06
Possibly try booting from another medium, e.g. a flash drive.

---

### Post by ioan1ioan on 2011-12-06
So the problem is due to hardware but not due to graphic card?

---

### Post by BC59 on 2011-12-06
It's not a hardware problem, but there is a hardware incompatibility, between your computer and Ubuntu.

---

### Post by ioan1ioan on 2011-12-06
And what should i do to solve it?

---

### Post by BC59 on 2011-12-06
Look [here]("http://ubuntuforums.org/showthread.php?t=1613132") if you can follow the instructions.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by oldtimer7777 on 2011-12-06
Just to be clear.. Wubi is more for test driving Ubuntu for a while.. It really isn't a great way to use Ubuntu on a long term basis, esp. if you begin putting more and more of your time into issues like this..  It is far superior to install Ubuntu side by side in its own dedicated partition on your HDD with either an installation disc of Ubuntu, or a live bootable USB Flash Drive of Ubuntu 11.10:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **ioan1ioan said:**
> Hi everyone,
i installed ubuntu (11.10) using wubi(download wubi and run it) through my win 7 proffesional. Everything during installation went ok, except from the end where the login screen appears and demands the password in order to login. Then after 10 at most seconds everything freezes and after some minutes computer shuts down. I tried to uninstall and re-install ubuntu several times but still the problem exists. Does someone knows what should i do? I am quite starter in using ubuntu so i would appreciate it if the instructions will be detailed.
Thanks.

PS: In that desktop i used to have windows xp / ubuntu 10.04 dual booting without any problem. Also the fan in graphic card is broken so i replace it with a universal one.

---

### Post by ioan1ioan on 2011-12-06
So you think that i won't have any problems if i install ubuntu with a usb stick?

---

### Post by ioan1ioan on 2011-12-07
Hi again,
i've got some news. I tried to install the kubuntu and during installatios i pressed esc and choos acpi(or something like that)
and the sceen didn't freeze as it used to do but a window appear which said that:

Loop-mounted file systems already present
The selected partition (partition 1 of /var/lib/partman/devices/=dev=sda) already containsthe following file system images:
/ubuntu/disks/root.disk
Please uninstall these before trying again.

I attach a picture of tha window.

What must i do now?

Thanks.

---

### Post by Mark Phelps on 2011-12-07
That file is the one that is installed using Wubi -- indicating that Ubuntu is already installed into that partition.

This time, instead of installing, boot normally and see if it gets into the OS selection menu (in Windows).  If Ubuntu is shown there, try it and see what happens.

If it then starts to load Ubuntu but crashes along the way, you should uninstall Ubuntu (using Programs and Features) and reinstall.

---

