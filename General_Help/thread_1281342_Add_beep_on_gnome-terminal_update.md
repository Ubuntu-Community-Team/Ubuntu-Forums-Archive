---
title: "Add beep on gnome-terminal update"
date: 2009-10-03
forum: General Help
---

### Post by mdaud on 2009-10-03
I would like to have a beep sound on each terminal status update, such as tail -f or even any kind of new line of any stdout.
I know many will say that beep is annoying but its easy to change beep freq. and giv it some nice settings.

currently I use this command
tail -F /var/log/syslog | beep -s -f 12000 -l 50

but this is only work on my own machine. so if I ssh to remote host this wont work which I need it deadly.
any suggestion?

---

