---
title: "Firefox going dark for 10-20 seconds"
date: 2011-05-28
forum: General Help
---

### Post by scoopjones on 2011-05-28
I'm having a problem with Firefox going dark (application so busy it stops responding) while it is loading web sites. When I switch to the terminal and do "top", it shows "compiz" and "Xorg"  as the most busy applications. I'm using Ubuntu 10.10 and Firefox 3.6.17. Anyone have an idea of what might be causing this?

Thanks,
Evan Jones
[EMAIL="scoopjones@yahoo.com"]scoopjones@yahoo.com[/EMAIL]

---

### Post by skumara on 2011-05-28
> **scoopjones said:**
> I'm having a problem with Firefox going dark (application so busy it stops responding) while it is loading web sites. When I switch to the terminal and do "top", it shows "compiz" and "Xorg"  as the most busy applications. I'm using Ubuntu 10.10 and Firefox 3.6.17. Anyone have an idea of what might be causing this?

Thanks,
Evan Jones
[EMAIL="scoopjones@yahoo.com"]scoopjones@yahoo.com[/EMAIL]

use this and see what firefox is doing and post it here

```
ps aux | grep firefox
```

---

### Post by lovinglinux on 2011-05-28
Could be some extension performing a slow action when loading a new page. Start Firefox in safe mode and check if the problem persists:

```
firefox -safe-mode
```

I also recommend getting Firefox 4, which has a much faster javascript engine. See these:

[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)
[http://www.webgapps.org/tutorials/firefox/general/installing-other-versions](http://www.webgapps.org/tutorials/firefox/general/installing-other-versions)

Also check my tutorials on [Firefox optimization]("http://www.webgapps.org/tutorials/firefox/optimization").

---

### Post by linuxinstalledfromhdd on 2011-05-28
Also I would recommend cleaning out firefox with bleachbit. You can install it from terminal:

sudo apt-get install bleachbit

Great cache cleaner.  Sometimes that helps when I have had this issue too. :)

---

### Post by lovinglinux on 2011-05-28
> **linuxinstalledfromhdd said:**
> Also I would recommend cleaning out firefox with bleachbit. You can install it from terminal:

sudo apt-get install bleachbit

Great cache cleaner.  Sometimes that helps when I have had this issue too. :)

BleachBit can also vacuum FF databases, which can improve performance considerably.

---

