---
title: "No Startup Applications"
date: 2011-10-23
forum: General Help
---

### Post by Seraphim9 on 2011-10-23
[FONT=Book Antiqua][SIZE=3]So I upgraded from 11.04 to 11.10 via the Update Manager and so far so good except for the fact that when I open Startup Applications there is only **one** listed (Evolution Alarm Notify). Where did all the others go? Has anyone else experienced this and have a fix/workaround? Thanks in advance.[/SIZE][/FONT]

---

### Post by haqking on 2011-10-23
> **Seraphim9 said:**
> [FONT=Book Antiqua][SIZE=3]So I upgraded from 11.04 to 11.10 via the Update Manager and so far so good except for the fact that when I open Startup Applications there is only **one** listed (Evolution Alarm Notify). Where did all the others go? Has anyone else experienced this and have a fix/workaround? Thanks in advance.[/SIZE][/FONT]

yes it is supposed to be that way.

they are in a autostart folder now, with a .desktop extension.

Part of the config is NoDisplay=true statement which you need to change to false if you want it listed.

Edit. Link for more information. [http://askubuntu.com/questions/66910/what-happened-to-to-the-startup-application-preferences](http://askubuntu.com/questions/66910/what-happened-to-to-the-startup-application-preferences)

Peace

---

### Post by Seraphim9 on 2011-10-24
[SIZE=3]This was done on purpose!? Lame. Thanks for the link, it worked like a charm. Thanks for pointing me in the right direction haqking. Cheers!
[/SIZE]

---

### Post by haqking on 2011-10-24
> **Seraphim9 said:**
> [SIZE=3]This was done on purpose!? Lame. Thanks for the link, it worked like a charm. Thanks for pointing me in the right direction haqking. Cheers!
[/SIZE]

no worries you are welcome

peace

---

