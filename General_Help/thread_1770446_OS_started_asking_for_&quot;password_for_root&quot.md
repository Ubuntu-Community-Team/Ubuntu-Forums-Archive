---
title: "OS started asking for &quot;password for root&quot; rather than sudo"
date: 2011-05-29
forum: General Help
---

### Post by nottrobin on 2011-05-29
Recently, when I try to do admin tasks - e.g. setting my wireless connection to "available to all users" or updating a group's settings - it asks for "password for root" rather than asking for my password so it can sudo.

I was forced to enable the root password, so I could do anything on my system ( sudo su; passwd; ) but I'd rather keep my root password locked and use sudo if possible.

This seemed to happen after my computer crashed and I had to do a hard reboot. This might be related.

Does anyone know why this might have happened?

---

### Post by WorMzy on 2011-05-29
One of your gconf keys has become switched. Run gksu-properties (as your normal user) and switch it from su mode to sudo.

---

### Post by nottrobin on 2011-05-31
Yeah I discovered my user had actually got removed from "admin" and "sudo" groups. Adding them again fixed it.

---

### Post by MWetzel65 on 2011-05-31
Total NOOB in Linux here. Would this method work to give me FULL administrative privileges? Copying and pasting to "root" folders for example?

---

### Post by mcduck on 2011-05-31
> **MWetzel65 said:**
> Total NOOB in Linux here. Would this method work to give me FULL administrative privileges? Copying and pasting to "root" folders for example?

Using Ubuntu's default security model (with admin users that have sudo access instead of an active root account) already gives you that ability.

There are very, very rare things (if any) that would require using root directly instead of using sudo.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

If you need to write to system directories just use sudo from command line, or run "gksudo nautilus" to open the file manager with root permissions. There's also the "nautilus-gksu"-pacakge which adds the option to open a location as root into the right-click menu in filemanager.

---

