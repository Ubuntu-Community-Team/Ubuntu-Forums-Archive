---
title: "origami/Folding@Home cannot reinstall"
date: 2010-03-06
forum: General Help
---

### Post by MikeEagling on 2010-03-06
I've been running Folding@Home by using Origami but have run in to trouble.

I have tried to change my team using "sudo origami -name -u USERNAME -t TEAM" but it didn't seem to work.

After several attempts I figured I'd just reinstall but now, no matter what I try, I can't get it to work.

I've tried "remove" and "purge" options in apt-get. I've even tried manually removing every reference to "origami" I can "find" on my system but now, whenever I try "sudo origami install", I get the following error:

/usr/bin/origami: line 593: /var/lib/origami/client.cfg: No such file or directory
/usr/bin/origami: line 625: /var/lib/origami/origami.cron: No such file or directory
rm: cannot remove `/var/lib/origami/origami.cron': No such file or directory
WARNING: UNABLE TO DELETE INITIAL CRON FILE
ERROR: CAN NOT CHANGE INTO DIRECTORY: /var/lib/origami!

Does anyone know how to fix this?

---

