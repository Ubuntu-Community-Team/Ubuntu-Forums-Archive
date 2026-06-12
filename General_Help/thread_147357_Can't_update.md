---
title: "Can't update"
date: 2006-03-20
forum: General Help
---

### Post by rucker on 2006-03-20
The software updates manager no longer works.  It shows two updates:  one for dhcp3-client and one for dhcp3-common.  When I click "Install" the buttons grey out but nothing ever happens beyond that.

I have been trying every day for about a week.  I haven't had any problems until this and there are no other issues I can identify.  Any ideas?

---

### Post by rucker on 2006-03-20
I just did an "apt-get upgrade" and it worked fine.  The problem just seems to be with the gnome update manager that pops up on the toolbar :confused:

---

### Post by Klejs on 2006-03-20
Have you checked your sources.list?

Check it by typing:
```
sudo apt-get update
```

In an terminal.

Have fun!

---

### Post by Klejs on 2006-03-20
Ok, good that the problem is gone

---

### Post by mr.p on 2006-03-20
[QUOTE=rucker]The software updates manager no longer works.  It shows two updates:  one for dhcp3-client and one for dhcp3-common.  When I click "Install" the buttons grey out but nothing ever happens beyond that.

I have been trying every day for about a week.  I haven't had any problems until this and there are no other issues I can identify.  Any ideas?[/QUOTE]
Do the following to bring your system up to date via the terminal.

```

sudo apt-get update
sudo apt-get upgrade

```

And then try the Gnome update manager might just be a glitch with updating your sources.list.

---

### Post by MichaelZ on 2006-03-20
[quote=rucker]The software updates manager no longer works.  It shows two updates:  one for dhcp3-client and one for dhcp3-common.  When I click "Install" the buttons grey out but nothing ever happens beyond that.

I have been trying every day for about a week.  I haven't had any problems until this and there are no other issues I can identify.  Any ideas?[/quote] 
I have had/have (?) the same problem as you. Updates manager worked fine, then when I have tried to install the updates for the security issues, it greyed out. Re-booting the system was for me the solution (dirty-quick solution :)). Anyway, now it seems to re-work even if I do not have a lot of updates to install :).

Best wishes,
Michael

---

