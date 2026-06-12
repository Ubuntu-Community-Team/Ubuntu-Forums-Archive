---
title: "Shutdown procedure kind of messed up"
date: 2011-04-22
forum: General Help
---

### Post by DrScum on 2011-04-22
Problem: when trying to shutdown the system using the menue item or the icon NOTHING happens most of the times. The only way (I know of) in these cases is to open a terminal and type "sudo halt".

I tried but was not successful in diagnosing what causes this behaviour. A wild guess is that whenever I log on to a samba share and whenever I selected an operation which requires authentication (such as using synaptic) logging out a standard user is no longer possible.

Anybody out there who has a solution to this?

---

### Post by dino99 on 2011-04-22
are you using a remote desktop ? do you have administrative rights ?

first try to clean the system: gconf-cleaner & bleachbit
then update/install -f/configure -a

---

### Post by DrScum on 2011-04-23
I do not use a remote desktop.
I do have administrative rights

Are "gconf-cleaner & bleachbit"
and "update/install -f/configure -a"

terminal commands I should enter in order to do what you suggested?

---

### Post by psihokiller4 on 2011-04-23
have you tried
"sudo shutdown now"
"sudo shutdown -h"
you can try

man shutdown
or
shutdown man

as I'm not 100% for this atm i'm at win :(


but I never used sudo halt

---

### Post by DrScum on 2011-04-23
psihokiller4, there is no problem with the shutdown ittself. It's just annoying to have to open a terminal and type in a command, when there is a shutdown icon on the menue. 
And yes, I also have thought about writing a shutdown skript, but these are all workarounds around the real problem which I think should be solved anyway since there might be less experienced users trying to shutdown their machines using the icon the system offers.

---

### Post by psihokiller4 on 2011-04-23
ok now I get it

well that icon and than shut down must refer to certain file i don't know witch but that file has to have executable for all users (owner;group;others)

have you been playing with any file premisions?

---

### Post by DrScum on 2011-04-23
well, I constantly have problems with file permissions, e.g. when I copy to or from samba shares. I am not aware of having changed any permissions of system files.

---

