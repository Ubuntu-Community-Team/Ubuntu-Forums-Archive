---
title: "Oops! Just erased my /var/run/"
date: 2009-07-30
forum: General Help
---

### Post by harry71194 on 2009-07-30
Okay.. so I was messing with fail2ban last night.. it was 4 AM, and I was sleepy... so I hit the enter key on `sudo rm -rf /var/run/', before I tabbed to fail2ban to erase those files in fail2ban ... so ..... now I can not attach screens anymore, etc. Is there a simple command I can run to attempt to rebuild all my stuff there? I do not want to have to reinstall Ubuntu on this server :(

> harry@ubuntu:~$ sudo rm -rf /var/run
rm: cannot remove directory `/var/run': Device or resource busyWhoops! ^

screen -ls shows me as using no screens. Yet, irssi is still running on the screens (and if I highlight myself in IRC, it still notices me my away message)... so I know there is some way to recover everything I erased.


Help me out of this sticky situation please.

---

### Post by kerry_s on 2009-07-30
just reboot, /var/run is created a startup.

you should be more careful, next time i doubt you'll be so lucky.

---

### Post by PurposeOfReason on 2009-07-30
Nevermind. Use backups from now on for important things you might delete.

---

### Post by harry71194 on 2009-07-30
> **kerry_s said:**
> just reboot, /var/run is created a startup.

you should be more careful, next time i doubt you'll be so lucky.
Thanks, worked :)

---

