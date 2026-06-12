---
title: "Cron-ically desperate"
date: 2010-03-12
forum: General Help
---

### Post by Langstracht on 2010-03-12
If I understand correctly my cron file is in the tmp folder.

A (manual) command entered while in the tmp folder works just fine.

However in the cron file it does not.

Not sure that it should matter but the command is "nautilus ~/Directory/SubDirectory"

Thanks in anticipation of any help.

---

### Post by rnerwein on 2010-03-12
hi
that is because nautilus need a DISPLAY and the second crons PATH is only /bin and /usr/bin 
make a script called "my_cron_script" make it executable ( chmod 755 my_c.... ) and place it in your
/home/xxxx/bin
your crontab entry then looks like: 22 17 * * * /home/xxxx/bin/my_cron_script

contents of my_cron_script:
#!/bin/bash
DISPLAY=:0.0
export DISPLAY
/usr/bin/nautilus

ciao

---

### Post by Langstracht on 2010-03-12
Thanks for that.  Works like a charm.

---

