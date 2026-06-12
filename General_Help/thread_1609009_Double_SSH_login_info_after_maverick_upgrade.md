---
title: "Double SSH login info after maverick upgrade"
date: 2010-10-29
forum: General Help
---

### Post by nunyez on 2010-10-29
When I login via ssh I get both post and pre-upgrade information...?

```
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Fri Oct 29 20:17:42 EDT 2010

  System load:    0.24               Temperature:         40 C
  Usage of /home: 79.9% of 79.37GB   Processes:           205
  Memory usage:   42%                Users logged in:     1
  Swap usage:     0%                 IP address for eth0: 192.168.1.10

  Graph this data and manage this system at https://landscape.canonical.com/

Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Thu Oct 21 18:34:22 EDT 2010

  System load:    0.3                Temperature:         40 C
  Usage of /home: 79.9% of 79.37GB   Processes:           230
  Memory usage:   51%                Users logged in:     1
  Swap usage:     29%                IP address for eth0: 192.168.1.10

  Graph this data and manage this system at https://landscape.canonical.com/

926 packages can be updated.
0 updates are security updates.

New release 'maverick' available.
Run 'do-release-upgrade' to upgrade to it.

*** System restart required ***

```

---

### Post by ThePol1 on 2010-10-29
Maybe edit the SSH message of the day?

sudo gedit /etc/motd

---

### Post by a-user on 2010-11-04
i have the same issue. i observed the following odd things:
1. i had printmotd set to no in sshd_config but i still got the login message no matter what was in motd
2. i changed printmotd option to yes and edited /etc/motd. result: i got the original logn message twice
3. i rechecked /etc/motd and saw that my changes were lost, i mean it allways gets overwritten with the feault ones imediatly, or when i attempt to login.

so, wihtout printmotd set to yes i get only one message, the default one.
with printmotd to yes i get the default one twice, no matter what content is in motd, it get reverted.

---

### Post by a-user on 2010-11-04
found the solution/reason.
ubuntu has now an automated cron job for updating and modifying motd.

see [http://manpages.ubuntu.com/manpages/intrepid/man1/update-motd.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/update-motd.1.html).

you must set printmotd to no in sshd_config, otherwise you get the motd file printed double. how you could disable motd printing at all... well i dont know. but if you follow my link you will see how to modify the content.

---

