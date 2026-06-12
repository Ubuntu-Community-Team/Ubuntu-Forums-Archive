---
title: "Ubuntu wont load"
date: 2009-10-10
forum: General Help
---

### Post by jbjmed on 2009-10-10
hope you all can help me. 

i have been running ubuntu 9.04 for about a month with no problem. my first time ever using linux and its great. ok so heres my problem. after a forced shut down and restart i got a message to run fsck. i have done so in the past and it worked out fine, only this time after putting in my name and password it just hangs. i can load in failsafe/gnome but wont load as usual. 

Thanks for anyhelp.

---

### Post by jbjmed on 2009-10-11
any body? there are no error messages. it just hangs.

---

### Post by tuxxy on 2009-10-11
Boot from the LiveCD then open a terminal and run

```
sudo fsck /dev/sda1
```You may need to edit the last part of the command depending on your partition name.  Once its done reboot the machine and login as normal.

---

