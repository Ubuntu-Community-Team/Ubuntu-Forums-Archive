---
title: "Boinc not displaying correctly after boot/reboot"
date: 2012-01-04
forum: General Help
---

### Post by Kevbert on 2012-01-04
Hi. I'm running Boinc version 6.12.33 x86_64-pc-linux-gnu on a Intel 64X2 system with Xubuntu version 3.0.0-14-generic x86_64. I normally run Boinc in advanced display mode (i.e. the one that displays a table of project tasks). On shutdown I leave the Boinc window open.
When I reboot I get the display shown below.  The only way to get Boinc to display correctly is to end the process in terminal with
```
top
```
and then 
```
sudo kill *process_numbers_for_Boinc*
```
prior to restarting Boinc from the menus.
Any suggestions ?

---

