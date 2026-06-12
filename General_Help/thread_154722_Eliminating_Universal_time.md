---
title: "Eliminating Universal time"
date: 2006-04-03
forum: General Help
---

### Post by johnfw7 on 2006-04-03
When installing Kubuntu I pressed the 'uses UTS' in error.

Using root I have not been able to delete UTS as the time zone.

What configuration file or other method will allow me to correct the problem.

Reguards

johnfw

---

### Post by FlakJacket on 2006-04-03
go into a console like konsole and type in ```
tzconfig
``` then follow the prompts and you should be ok.

Hope that helps,
Flak

---

### Post by johnfw7 on 2006-04-03
Thanks, I tried tzconfig

Unfortunately it doesn't let you do anything to UT, you can do no more than the time settings in kde

So I still have it resetting EST to UT on close

---

### Post by incubus on 2006-04-03
I'm almost sure this is not the Debian way of doing it, but here's what I did to go in the opposite direction:

$ sudo vi /etc/default/rcS

Switch the UTC flag. You probably need to reboot (to run the initscripts).
I'd be curious myself to learn the elegant way of doing this.

incubus

PS: Just curious, you ran 'tzconfig' with sudo, right? You probably know that you can have the time set to UTC, but have the timezone adjusted accordingly. This is the convention in Unix, but Windows doesn't play well with it.

---

### Post by johnfw7 on 2006-04-04
That worked perfectly. Thanks

UTS was causing inconvenience to programs in other partitions without any benifit to me

johnfw

---

