---
title: "how to DISABLE suspend in 6.06"
date: 2006-06-17
forum: General Help
---

### Post by lex1 on 2006-06-17
I havea labtop with fluxbox when computer goes into suspend after about 30 to 45 minutes of inactivity this kills ssh and i cannot conect from remote host.

I have seen this in the wiki(see below) but how to disable suspend?

lex1

ACPI

To suspend to disk, choose "Hibernate" from the GNOME logout menu. To suspend to RAM, edit

/etc/default/acpi-support

and uncomment the second line by deleting the # character, to read:

ACPI_SLEEP=true 

Ubuntu 6.06

Dapper needs another step to enable suspend. Execute gconf-editor, and visit apps/gnome-powermanager and enable "can_suspend". You can enable/disable suspend and/or hibernation from there.

---

### Post by vigleik on 2006-06-17
I'm not sure if this is what you're looking for, but you can change a couple of settings with "gnome-power-preferences". This affects gnome-power-manager, which seems to be running even if you're not using gnome.

Vigleik

---

### Post by lex1 on 2006-06-17
what are the prefrences please.
please note i did not suspend the labtop did it automatically

---

### Post by vigleik on 2006-06-17
[QUOTE=lex1]what are the prefrences please.
please note i did not suspend the labtop did it automatically[/QUOTE]

Type "gnome-power-preferences" in a terminal, you'll get a window with a couple of settings. I'm not sure if this is what's causing your problem, only that it was still running under kde for me and caused me some problems.

---

