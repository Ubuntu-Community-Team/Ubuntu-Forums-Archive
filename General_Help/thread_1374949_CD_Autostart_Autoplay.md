---
title: "CD Autostart Autoplay"
date: 2010-01-07
forum: General Help
---

### Post by junovo on 2010-01-07
Hi 

I wanted to create a CD that when place in the drive will automatically open a HTM file etc. I know that I cant use the standrad autorun.inf that is used on windows so need help as cannot find any applications. 

thanks 
rob

---

### Post by chewearn on 2010-01-07
By design in Ubuntu, I don't think this is possible.  It's a security risk to allow a CD to dictate an action to be performed by the computer.

---

### Post by mc4man on 2010-01-07
You can do some/all of what you asked if...
you use a script to do what you want -( open a HTM file in this case

And this is intended only for use on your machine(s)

A file named autorun on the cd is needed to initiate the action. It can be empty or could contain a script that causes the intended result

As far as autoplay, by default that's disabled in regards to software on removable media, but can be enabled. Also by default, even when enabled, there is no choice to 'run' the software (script) but again that's relatively easy to work around.

The basic flow is cd inserted with a autorun file which initiates "x-content/software=" which the default action is set to a .desktop in which the EXEC= is either a local script or loops back to the cd -  /media/cdrom/script

---

### Post by chewearn on 2010-01-08
My point is, you cannot make a CD that auto-magically tells Ubuntu to do something on loading.

Of course, I am not excluding ability to tinker with Ubuntu to initiate "run a script" on CD insert.  In this instance, the CD autorun would work on one PC.

---

### Post by junovo on 2010-01-08
Hi 

Thanks for the replies. I think its important for the future that something is devised as will be more user friendly and helpfull for distributing applications

---

