---
title: "help... no privileges"
date: 2009-08-22
forum: General Help
---

### Post by AmerNewbieInDE on 2009-08-22
how do i get my privileges back, can use internet, printer.. nothing

---

### Post by michy99 on 2009-08-22
A few details, please. Give an example of something you are trying to do, and what happens when you try.

---

### Post by AmerNewbieInDE on 2009-08-22
i i cant print, connect to the internet, i cant open users....  i cant admin the pc,  i tried sudo users-admin, i tried gksudo users-admin, the error is, can not access the resorces, you dont have permission...

---

### Post by BackwardsDown on 2009-08-22
When you click on Firefox? It sais that you don't have permission to access the internet? Or when you press the print button a dialog pops up? 

Tell us what's on your screen and what you have tried. And is this since a few days? Or is this the first time that you use Ubuntu?

---

### Post by michy99 on 2009-08-22
Open up a terminal and enter this:```
groups
```What do you get as output?

---

### Post by AmerNewbieInDE on 2009-08-22
it took my network connection away, and i cant put it back. to shut down, i have to hit ctrl+alt+del to shutdown, but it only goes back to the login screen, thne i can choose to shutdown

the file shows me as william root adm dialout fax cdrom tape audio dip video plugdev fuse lpadmin netdev admin sambashare vboxusers

but in reality, i am restricted user...

---

### Post by michy99 on 2009-08-22
What does your sudoers file look like?```
sudo cat /etc/sudoers
```

---

### Post by AmerNewbieInDE on 2009-08-22
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

---

### Post by michy99 on 2009-08-22
Well you are a member of the admin group, and sudoers looks right, so I don't know what the problem is.

---

### Post by Hendrixski on 2009-08-22
That's really odd. I've never heard of such a thing, not having permissions to access the internet?

How did this happen? were you running you system under root user and mess something up?

You rebooted and this persists?

Did you google the error message that it gives you when it tells you that you don't have permissions?


How are you accessing these forums if you can't go online?

---

### Post by AmerNewbieInDE on 2009-08-22
i had no permission to set up the internet connection, could not run su, sudo, or gksudo.. i gave up, i am currently reinstalling everything.. i didnt mess anything up as root, i only use it IF i have to, and not to play...

---

