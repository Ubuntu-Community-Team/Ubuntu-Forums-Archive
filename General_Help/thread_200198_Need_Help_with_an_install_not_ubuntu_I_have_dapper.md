---
title: "Need Help with an install not ubuntu I have dapper already"
date: 2006-06-19
forum: General Help
---

### Post by Drifter on 2006-06-19
I downloaded crossover office demo, but I have no idea how to install it.  I have read post in the forum but still need help.  Can anyone point me to a how to or just walk me through it.  Thanks

---

### Post by xXx 0wn3d xXx on 2006-06-19
[QUOTE=Drifter]I downloaded crossover office demo, but I have no idea how to install it.  I have read post in the forum but still need help.  Can anyone point me to a how to or just walk me through it.  Thanks[/QUOTE]
What type of file is it ? If it's icon looks like a scroll, type:
> cd /path/where/the/script/is/
(If it on your desktop, cd /home/$USER/Desktop) You can replace $USER with your username but it will work with the $User command.
> sudo ./ crossoveroffice
replace crossover office with the name of the file.

If it doesn't work, try this and then retry the steps above:
> sudo chmod 777 /path/to/crossover/office/file

---

