---
title: "sudo nautilus changes desktop??"
date: 2009-07-08
forum: General Help
---

### Post by abhilashm86 on 2009-07-08
when i type sudo nautilus  to modify some files, then ubuntu desktop changes and when i close also, desktop wont change..............
how to recover this??

---

### Post by renzokuken on 2009-07-08
you should be able to just restart the x server (or even reboot) and it will sort it.

for future reference though......you shouldnt use 'sudo' to open graphical applications. the proper way to do it is using

```
gksudo nautilus
```

this should also prevent the problem you are having

---

### Post by abhilashm86 on 2009-07-08
> **renzokuken said:**
> you should be able to just restart the x server (or even reboot) and it will sort it.

for future reference though......you shouldnt use 'sudo' to open graphical applications. the proper way to do it is using

```
gksudo nautilus
```

this should also prevent the problem you are having

thanks now its working fine, how to just restart x server??
i tried now ```

abhilash@abhilash:~$ sudo startx


Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.



```
its ok, i'll restart system itself, but how to just re boot x server??

---

### Post by renzokuken on 2009-07-08
to restat X you used to be able to just hit Ctrl+Alt+Backsapce but i believe they disabled that in jaunty.

the other way is to get to a tty screen using Ctrl+Alt+F1 (or F2, F3 etc) and then run

```
sudo /etc/init.d/gdm restart
```

---

