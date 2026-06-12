---
title: "admin issues with version 10.04"
date: 2010-07-12
forum: General Help
---

### Post by lord_arnum on 2010-07-12
since i have upgraded my Ubuntu version to 10.04, anything concerning administrative services i can no longer run. i have already verified that i still have full admin access, but i cant get anything on my admin tab to open or function. i've already tried the 10.04 fix, but to no avail. any new suggestions? if not is there a way i can go back to 9.10 without losing my data?

---

### Post by sisco311 on 2010-07-13
Hi and welcome to the forums!

We need a little bit more information. What's the output of:
```
groups
```
```
sudo echo sudo
```
```
sudo cat /etc/sudoers
```

```
pkexec echo policykit
```
and
```
ps -ef | grep polkit
```?

---

### Post by lord_arnum on 2010-07-13
hello sisco311. thanks for helping me here. 

here is the outputs you were looking for:
\jason@Kamiyosha Technological Laboratories:~$ groups
jason adm dialout cdrom audio plugdev fuse lpadmin netdev admin sambashare guest
jason@Kamiyosha Technological Laboratories:~$ ^C
jason@Kamiyosha Technological Laboratories:~$ sudo echo sudo
sudo: unable to resolve host Kamiyosha Technological Laboratories
[sudo] password for jason: 
sudo
jason@Kamiyosha Technological Laboratories:~$ sudo echo sudo
sudo: unable to resolve host Kamiyosha Technological Laboratories
sudo
jason@Kamiyosha Technological Laboratories:~$ sudo cat /etc/sudoers
sudo: unable to resolve host Kamiyosha Technological Laboratories
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
jason@Kamiyosha Technological Laboratories:~$ pkexec echo policykit
policykit
jason@Kamiyosha Technological Laboratories:~$ ps -ef | grep polkit
root      1343     1  0 15:34 ?        00:00:00 /usr/lib/policykit-1/polkitd
jason     1548  1462  0 15:35 ?        00:00:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
jason     2275  2239  0 17:39 pts/0    00:00:00 grep polkit
jason@Kamiyosha Technological Laboratories:~$ 

i hope that will help. thanks again.

---

### Post by sisco311 on 2010-07-13
Hi lord_arnum,

Hmmm, everything looks fine, could you please elaborate your problem?

---

### Post by prodigy_ on 2010-07-13
> **lord_arnum said:**
> i cant get anything on my admin tab to open or function.
Admin tab? What's that?

Anyway, if **sudo -i** works, you can do anything you want from root shell (just as in any other version of Ubuntu).

---

### Post by lord_arnum on 2010-07-14
ok. i will elaborate. lets say that i want to do an update. i click on the update now button (in update manager) and the tack manager has a tab that states "starting administrative services" a few seconds pass and then that tab closes. absolutly nothing else happens. i then have to force quit the application. this has occurred to every program that has opened the "starting admin services" tab. tab closes, program fails to open or it freezes and requires me to force quit it. due to this, anythinf under "system /administration" no longer works. since i am still learning how to navigate the world of Terminal (even have a book on Unix /Linux Terminal) this has been the worst thorn in my side.

---

### Post by JKyleOKC on 2010-07-15
Could it be that those blank spaces in your hostname are confusing the sudo program? Your error messages indicate that there's some problem of that sort involved...

---

