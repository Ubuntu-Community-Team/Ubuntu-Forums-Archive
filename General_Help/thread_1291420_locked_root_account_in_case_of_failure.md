---
title: "locked root account in case of failure"
date: 2009-10-14
forum: General Help
---

### Post by Steinar on 2009-10-14
Greetings,

I just had an Xubuntu install that more or less broke down.  It was running the latest development Karmic, and I knew the risks involved.

Anyway, on boot, fsck started complaining about errors and gave up, and sent me to the maintenance shell.  I had to run fsck manually, first with no options, but that didn't fix it so on the next boot I had to run "fsck -a" before I could reboot successfully.

My question is, would this be possible with the locked root account that is now the default?  Would my (only) user's password be accepted when the system is in trouble like this?  I'm not talking about going into single user mode by choice.

Thanks!

---

### Post by sisco311 on 2009-10-14
Yes, sulogin is patched in Ubuntu, if the root account password is locked, then you are dropped into a BusyBox shell without being asked for a password.

---

