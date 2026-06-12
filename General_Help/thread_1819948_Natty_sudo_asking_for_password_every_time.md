---
title: "Natty sudo asking for password every time"
date: 2011-08-07
forum: General Help
---

### Post by mixmastamyk on 2011-08-07
Does anyone know if this has changed or was broken in Natty? on Maverick it worked as expected, with sudo only asking for the password every 5 minutes or so.

I followed these instructions, didn't work:
  [https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

I then followed these:
[http://superuser.com/questions/297566/sudo-keeps-asking-me-for-my-password](http://superuser.com/questions/297566/sudo-keeps-asking-me-for-my-password)

Didn't help either.  :/

---

### Post by mc4man on 2011-08-07
In natty (sudo 1.7.4+), the 'timeout' will only apply to the instance that was authenticated.
So when you close that terminal the next one you open will again require auth., ect.
There is a way to get around this, (!tty_tickets), but i don't particularly like it so instead I use the 1.7.2 from maverick security updates . 
(here i've set to only use password once per session for terminals,synaptic

Are you looking to change the default time (15 min. I believe), in addition to having work across all instances?

---

### Post by mixmastamyk on 2011-08-07
It's actually worse than that, it asks every single time in the same terminal.  I had an unmodified sudoers which worked fine in maverick and not in natty.

---

### Post by mc4man on 2011-08-07
Well - what do you want to do?

( - actually - here is a thread on, in post 21 I link to mavericks sudo package, (1.7.2) . After downgrading to have command to  use visudo to create and write a new timeout period in sudoers.d  - in this case using timeout of -1 which means never
(if you didn't want to change the timeout period then simply downgrading and rebooting will do..

In post 29 show how to use natty's sudo (1.7.4) and restore prior behavior using the no tty_tickets option, either in the sudoers file or my preferred of creating and using a file in sudoers.d instead.
Again adjusting the timeout period to never

I absolutely prefer the downgrade method over the no tty_tickets, also I prefer creating/using a file sudoers.d instead of sudoers

[http://ubuntuforums.org/showthread.php?t=1648577&page=2](http://ubuntuforums.org/showthread.php?t=1648577&page=2)

---

### Post by mixmastamyk on 2013-02-02
Sorry, at the time I didn't understand your answer about !tty_tickets and the new version of sudo.

Two years later I find it turns out this was an interaction with the fish shell.  More details here: [http://askubuntu.com/questions/106332/change-sudo-timeout-under-fish](http://askubuntu.com/questions/106332/change-sudo-timeout-under-fish).

I did put it into sudoers.d under Quantal! and all is good. :)

---

