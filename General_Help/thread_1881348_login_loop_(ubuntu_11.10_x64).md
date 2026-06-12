---
title: "login loop (ubuntu 11.10 x64)"
date: 2011-11-15
forum: General Help
---

### Post by rXp on 2011-11-15
Hi,

When I try to login I get redirected to the login screen. I tried to restart xorg I tried every solution I found on this forum. Nothing worked.
I even tried to reinstall ubuntu but 2 weeks after that the issue was back.

What can I do ?

Best regards,

rXp>!<

---

### Post by Wayne_V on 2011-11-15
is caps lock on?

did your default keyboard get changed?

have you tried a non graphical login (Ctrl-Alt-F1)

have you typed your password in the username field to make sure you don't have any non-functioning keys?

more details please!

---

### Post by rXp on 2011-11-15
> **Wayne_V said:**
> is caps lock on?

did your default keyboard get changed?

have you tried a non graphical login (Ctrl-Alt-F1)

have you typed your password in the username field to make sure you don't have any non-functioning keys?

more details please!
Caps lock is not on.
Didn't change the keyboard.
Yes I can log with the CTRL-ALT-F1
Yes I tried and I also tried to write it wrong to see the reaction.

---

### Post by Wayne_V on 2011-11-15
at the non-graphical login check for any errors:

as user:
$ tail ~/.xsession-errors

as root (sudo -s):
$ sudo -s    
# cd /var/log
# find . -ls | grep "Nov 15"

# tail <any files modified today>

also run "last" and "lastb" as root and check the output

---

### Post by rXp on 2011-11-15
I manage to resolve the issue.
Since I thought my issue came from an update of the system, I did a apt-get update and apt-get upgrade. I rebooted the computer and it worked :D

---

