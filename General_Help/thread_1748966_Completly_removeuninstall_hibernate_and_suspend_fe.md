---
title: "Completly remove/uninstall hibernate and suspend feature"
date: 2011-05-04
forum: General Help
---

### Post by alexan on 2011-05-04
There's a single command to achieve this result?
I want those (never and not willing to use in future) features to be completly remove from all my systems (*buntu).


:KS

Prefered command like **sudo apt-get autoremove** and avoid "*clicking/settting throug various menu*"
_Battery level indicator prefereably kept_

---

### Post by alexan on 2011-05-04
Forgot to say that any help is welcome :D

---

### Post by alexan on 2011-05-05
Let us free from the undemocratic hibernate/suspension feature. Still looking for! :confused:

---

### Post by alexan on 2011-05-06
For the solution, I am still looking for

---

### Post by alexan on 2011-05-09
freedom of choice, where are you?

---

### Post by alexan on 2011-05-10
Yes, still looking :)

---

### Post by alexan on 2011-05-12
daily bump

---

### Post by wilee-nilee on 2011-05-12
> **alexan said:**
> daily bump

So in less than about 6 min I found this on Google, using your header as a search, maybe you should try there as well next time, just saying.;)
[http://linuxexpresso.wordpress.com/2010/05/09/disable-suspend-and-hibernate-ubuntu/](http://linuxexpresso.wordpress.com/2010/05/09/disable-suspend-and-hibernate-ubuntu/)

---

### Post by alexan on 2011-05-12
> **wilee-nilee said:**
> So in less than about 6 min I found this on Google, using your header as a search, maybe you should try there as well next time, just saying.;)
[http://linuxexpresso.wordpress.com/2010/05/09/disable-suspend-and-hibernate-ubuntu/](http://linuxexpresso.wordpress.com/2010/05/09/disable-suspend-and-hibernate-ubuntu/)


> Completly **remove/uninstall** hibernate and suspend feature

Thanks for your time anyway. Still looking


Also this thread is on top of google search for "*remove hibernate ubuntu*". Solve there, solve for the future
Explication: a package name or stuff like probably that maintain the same name from varius distro (and even Ubuntu update version).
A "fixing" procedure, as well as menu settings, change/varies pretty easily == problems

---

### Post by alexan on 2011-05-14
Call for a solution, thanks

---

### Post by alexan on 2011-05-15
The truth is out there: let it come in!

---

### Post by alexan on 2011-05-16
Just an info:
**sudo apt-get autoremove acpi gnome-power-manager**
_don't work_


So... still looking.

---

### Post by alexan on 2011-05-19
Bump for the next generation of googler who are looking for this answer!

---

### Post by Hedgehog1 on 2011-05-19
To disable the **Suspend** and **Hibernate** options: 

```
sudo gedit /usr/share/polkit-1/actions/org.freedesktop.upower.policy
```
There are two sections in this file, the first for suspend and the second for hibernate.
Near the end of each section will be a line with:
```
<allow_active>**yes**</allow_active>
```
Change each of these from **yes** to **no**
```
<allow_active>**no**</allow_active>
```
After you save the changes and reboot, the power menu will no longer display **Suspend** and **Hibernate**. 

***The Hedge***

:KS

---

### Post by alexan on 2011-05-21
An interesting alternative to needed remove, thanks Hedgehog1. But this wouldn't work with many ubuntu derivative. Also, probably, ubuntu will change again policy and thus this procedure will become pretty obsolete with ocelot+ (as the *gconf way* is obsolete with narwhal right now)

Still looking for the complete remove/uninstall. Don't let the hopes die! :KS

---

### Post by Hedgehog1 on 2011-05-21
Let me try to understand, you are looking for a solution that will fix future versions of Ubuntu that have not been written yet AND that will work on all other distros, too?

If that is your goal, you need to do more work than 'bump' a thread.  This will require real R&D work on your part to create a solution like that and commit to updating it when new distros come out.


***The Hedge***

---

### Post by alexan on 2011-05-22
Nah, basically I just need to know which package or kernelmodule offer said service (hibernate/suspension) and them... **remove** it (optionally blacklist for the kernel module) for a widen angle possible of distro/derivative.


Power managment, screen saver, low battery energy shutdown etc < all these will not use hibernate/suspension for gnome, kde, xfce&co. All in one hit.


Anyway, I am not just bumping this thread... I am also looking for a solution by my own

Additionally.

---

### Post by Hedgehog1 on 2011-05-22
OK - that makes more sense.

Cool.


***The Hedge***

:KS

---

### Post by alexan on 2011-05-23
Great :)


...but still looking for... ):

---

### Post by alexan on 2011-05-24
Bump

---

### Post by linuxinstalledfromhdd on 2011-05-24
[FONT=Verdana]http://linuxexpresso.wordpress.com/2010/05/09/disable-suspend-and-hibernate-ubuntu/[/FONT]

---

### Post by alexan on 2011-05-27
I see that *disabling* is a quite popular choice: no surprise at all.


Still looking for remove: :KS

---

### Post by alexan on 2011-06-11
I had some tries, but still unable to "solve" things.

---

### Post by alexan on 2011-06-27
Aw, still looking.
After some test&try I still wasn't able to find the kernel module which take care of the hibernate and suspend feature u_u

---

### Post by jeremija on 2011-09-05
The link which linuxinstalledfromhdd recommended works at my PC (ubuntu 11.04), but I have tried the recommendation from the comments:

Save this as a text file in /etc/polkit-1/localauthority/50-local.d/ folder with .pkla extension. 
```
[Disable suspend]
Identity=unix-user:*
Action=org.freedesktop.upower.suspend
ResultAny=no
ResultActive=no
ResultInctive=no

[Disable hibernate]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultAny=no
ResultActive=no
ResultInctive=no
```

Works after restarting the gdm service.
```
sudo service gdm restart
```

---

### Post by alexan on 2011-09-05
@jeremija: thanks for providing YADF (Yet Another Disable Function), those that will come from google will find a sure and quick solution for it.



But this isn't the craved complete removal. The difference is quite simple: setting and configuration can be changed/fixed whatever during normal use (and usually void within next Ubuntu upgrade). A complete removal will be more effective.


Something like a sudo rmmod?

---

### Post by linuxuser12345 on 2011-09-05
If you want to remove the suspend/hibernate feature, you will have to do that in BIOS. Check through your BIOS for a way to deactivate this mode. I can't exactly tell you how to do it, because everyone's BIOS is different. Good luck. :)

---

