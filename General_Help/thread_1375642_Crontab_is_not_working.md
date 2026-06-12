---
title: "Crontab is not working"
date: 2010-01-08
forum: General Help
---

### Post by kameelperdza on 2010-01-08
My crontab looks like this...
 
 
 
# m h dom mon dow command
*/5 * * * * /etc/Anope/anope.chk >/dev/null 2>&1
0,10,20,30,40,50 * * * * /etc/eggdrop/Apie.botchk >/dev/null 2>&1
 
 
 
It does not work correctly. But when i type  /etc/Anope/anope.chk  then anope runs and the same to eggdrop.
 
The problem is that eggdrop and anope does not run when ubuntu reboots

---

