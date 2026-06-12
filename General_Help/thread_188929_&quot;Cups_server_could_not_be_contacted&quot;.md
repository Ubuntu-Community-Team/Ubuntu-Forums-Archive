---
title: "&quot;Cups server could not be contacted&quot;"
date: 2006-06-04
forum: General Help
---

### Post by evilgold on 2006-06-04
i finally baught a printer the other day, and I'm trying to get ubuntu to print to it over the network with samba, but whenever i go to System> Administration > Printers The only thing i get is "the cups server could not be contacted."

I've googled this error, and found its a somewhat common bug... but i havnt found any soultions to it. could anybody suggest a work around, or an alternat way of adding a samba printer?

---

### Post by marcog on 2006-06-04
Same problem here.

---

### Post by cbandeira on 2006-06-08
I had the same problem and found the answer here: [http://www.ubuntuforums.org/showthread.php?t=185476&highlight=cups+server+contacted](http://www.ubuntuforums.org/showthread.php?t=185476&highlight=cups+server+contacted)

It seems I messed up my cupsd.conf by trying to share the printer to a windows box :oops:. So I suggest you guys to restore your /etc/cups/cupsd.conf (you did back it up, didn't you?) and the restart the cups daemon with "sudo /etc/init.d/cupsys restart"

---

### Post by evilgold on 2006-06-08
[QUOTE=cbandeira]I had the same problem and found the answer here: [http://www.ubuntuforums.org/showthread.php?t=185476&highlight=cups+server+contacted](http://www.ubuntuforums.org/showthread.php?t=185476&highlight=cups+server+contacted)

It seems I messed up my cupsd.conf by trying to share the printer to a windows box :oops:. So I suggest you guys to restore your /etc/cups/cupsd.conf (you did back it up, didn't you?) and the restart the cups daemon with "sudo /etc/init.d/cupsys restart"[/QUOTE]

Untill the other day i didnt own a printer. I havnt messed with cups...ever, config files or anything.

---

