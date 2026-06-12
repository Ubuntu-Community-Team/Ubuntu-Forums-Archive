---
title: "closing a software causes the system to reboot"
date: 2012-03-04
forum: General Help
---

### Post by bigbamboo on 2012-03-04
Hi,
I have a problem: every time I quit some software (i.e. xbmc), even with the "kill -9" command, the system asks me whether to reboot or to quit the whole OS ("Shut down this system now?") and it continues asking me to shut down even if I click the "cancel" button on the window.
So I can do nothing else but reboot the system (more than one time as the system keeps asking me to shutdown/reboot at every reboot).

My system is a foxconn nt330i with ubuntu 11.10 and Unity as DE.

thanks fo any advice.

---

### Post by bigbamboo on 2012-03-04
update: on Gnome3 I have no problem.
I'll keep gnome3 from now on, waiting for help.

---

### Post by bigbamboo on 2012-03-12
update

this annoying behavior shows up with gnome 3 also and seems to be connected with xbmc.

---

### Post by winh8r on 2012-03-12
try using system monitor to kill the process.


or 

```
sudo apt-get install htop
```

select the process you want to kill hit F9 and then hit enter to kill it.

NOTE:
the kill -9 command cannot be blocked once invoked.

open terminal and enter:

```
man kill
```

for more info.

---

### Post by bigbamboo on 2012-03-13
thanks,
the problems seems related to dbus-daemon session.
I'll try your solution next time I've to quit xbmc.

---

### Post by bigbamboo on 2012-05-28
I installed Mate as Desktop Environment and now I have no problems at all so I think this issue is related to Ubuntu new DE (gnome 3.0 & unity).

---

