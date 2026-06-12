---
title: "Laptop suspends when disconnected from mains."
date: 2010-10-08
forum: General Help
---

### Post by al688 on 2010-10-08
I'm sure I've seen this on the forum regarding known issues with lucid but I can't seem to find it!  I'm running lucid x64 and every time I disconnect from the mains the laptop suspends without going to battery power.  Can anybody point me in the direction of the solution?

Thanks in advance.

---

### Post by pratikk on 2010-11-17
I have the same problem on a Compaq Presario V2000 running Lucid, but I'm seeing it reported on various hardware/release combinations. Two workarounds suggested on the forums and Launchpad have not worked for me. They are:

1. Run gconf-editor and go to --> apps --> gnome-power-manager --> actions
and uncheck the box labeled "event_when_closed_battery".

2. Run gconf-editor and go to apps/gnome-power-manager/general
and de-select the option use_time_for_policy

Hope they work for you.

---

