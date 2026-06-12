---
title: "Ignore Pressing of Power Button"
date: 2006-03-18
forum: General Help
---

### Post by MrPaul on 2006-03-18
How can I make ubuntu ignore the pressing of the power button?  Right now it shuts down when pressed.

If there is a command line option it would be preferred as this is running headless.

---

### Post by jpkotta on 2006-03-18
If ACPI is enabled, you can probably play with the files in /etc/acpi.  Specifically /etc/acpi/events/powerbtn.

---

### Post by dcstar on 2006-03-18
[QUOTE=MrPaul]How can I make ubuntu ignore the pressing of the power button?  Right now it shuts down when pressed.

If there is a command line option it would be preferred as this is running headless.[/QUOTE]
If it boots to Gnome:

System-Preferences-Power Preferences

---

### Post by MrPaul on 2006-03-18
Got it.  Just put an exit at the top of /etc/acpi/powerbtn.sh and I'm all good now.

---

