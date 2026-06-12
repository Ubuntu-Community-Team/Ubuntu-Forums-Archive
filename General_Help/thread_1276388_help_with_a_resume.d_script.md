---
title: "help with a resume.d script"
date: 2009-09-27
forum: General Help
---

### Post by utnubuuser on 2009-09-27
hello -- any chance of getting some help with a script to add to my resume.d files that operates at root level and issues the command _fan2_?

It has to be at root level though.
Usually I do **sudo su**,then **my password**, then **fan2** (which is an alias to start my laptop's fan at a low level - the full command is **echo level 2 > /proc/acpi/ibm/fan**) and again, it only works at root level.

I usually start the fan manually in gnome-terminal, and I'd like it to resume after suspend.

It would also be great if the script exited root, launches a terminal window and issues the command **sensors** 2-3 seconds after restarting the fan

Thanks

---

