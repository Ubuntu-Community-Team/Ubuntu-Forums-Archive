---
title: "XFCE &quot;crashes&quot; sometimes but no idea why - help"
date: 2012-01-11
forum: General Help
---

### Post by geekyhawkes on 2012-01-11
hey guys, 

so sometimes my xfce just crashes and drops me back to the login screen without any real reason (as i can see).  What log could i look at to try and work out what is the issue?  The machine isnt working especially hard at the time, either in Firefox or Libreoffice but it almost seems related to me typing lots followed by RETURN at which point sometimes i will back at the login screen.

Recently I have noticed that Scroll Lock seems to flash on my keyboard just before the crash once or twice as i press keys but not sure if it is related or not.  I dual boot and dont have the same issue in the other OS so im happy to rule out hardware (i think).

Im running 11:10 xubuntu 64 if that matters?

Thanks

---

### Post by Toz on 2012-01-11
I would look at the following files:

~/.xsession-errors.old
/var/log/syslog
/var/log/Xorg.0.log

Perhaps there is something in there that might help to identify the cause.

---

### Post by geekyhawkes on 2012-01-14
Thansk, no clues at the moment but it hasnt crashed for a while so i will check back if it does it again.

---

### Post by Hylas de Niall on 2012-01-14
I *think* this is an issue with 11.10. I have seen lots of reports of intermittent crashes for all flavours of 11.10 - i have had many of these myself on my desktop machine (which runs win7 very happily), and i've reverted to using 10.10 after trying different DE's, and a number of reinstalls of 11.10.
I should add though that 11.10 is 100% fine on my much less powerful netbook, right from installing the beta2 back at the beginning of October.

---

