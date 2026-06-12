---
title: "Nice Value... (priority)"
date: 2010-08-15
forum: General Help
---

### Post by jee_bee on 2010-08-15
I use script like this to start gaming server....
> /bin/echo -e "\033]2;GunGame\007\c"
cd /media/server/srv1/srcds/orangebox
./srcds_run -console -game cstrike +map gg_ar_desert_outpost -maxplayers 20 -pingboost 3 -tickrate 66 -autoupdate

What nice or renice command do i have to add to change the nice value on server startup to -1 or less  ?

(srcds is creating 2 process on when starting it...
srcds_run and srcds_linux i dont know if it need a command for 
each or it will be automaticly set equal ??):confused:(??

---

