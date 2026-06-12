---
title: "hplip plugin"
date: 2011-10-03
forum: General Help
---

### Post by artantaaa on 2011-10-03
[SIZE=2]Hello. I recently got a hp laserjet 1000. When I plugged it in, hplip attempted to download a plugin from openprinting.org necessary to get it working. It failed because the openprinting.org site was down. I thought I would just try again later but it's been down for weeks now. I found the current version of the plugin ([/SIZE][SIZE=2][COLOR=black]hplip-3.11.7-plugin.run) at hplipopensource.com, but my system won't use it. It says that it needs [/COLOR][/SIZE][SIZE=2][COLOR=black]hplip-3.10.2-plugin.run, and I can't find that version anywhere. Does anyone know how I can get my printer to work?[/COLOR][/SIZE]

---

### Post by nomko on 2011-10-03
First of all, remove the old hplip driver using synaptic. After removing the hplip open a terminal and type this command: **sudo apt-get purge hplip* **(this will remove all remaining hplip packages left).
 
Then download the latest hplip driver from [www.hplipopensource.com]("http://www.hplipopensource.com"). Open a terminal and execute the .run file. Follow the installation instructions!
 
It is important to remove all old hplip packages since this migth be the source of the problem. During the installation, do not switch on your printer, at the end of the installation you can restart your computer.

---

### Post by artantaaa on 2011-10-03
Thanks. I'll try using the current version of hplip. Is there a reason that Ubuntu doesn't use the current version by default?

---

### Post by drs305 on 2011-10-03
I have a LaserJet 1000 and have tweaked it through all versions since Edgy. Sometimes it's harder than others, but I've always gotten it to work one way or another. 

I'm currently on Oneiric and used the same procedures outlined by *nomko*, although I generally use CUPS or foomatic.

---

