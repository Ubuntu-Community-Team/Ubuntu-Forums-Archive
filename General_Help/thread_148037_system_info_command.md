---
title: "system info command"
date: 2006-03-21
forum: General Help
---

### Post by macm10 on 2006-03-21
does anyone know what the command is to find out info about proc. and ram in the terminal. i used to know it but i forgot.

---

### Post by gnu2tux on 2006-03-21
cat /proc/cpuinfo
cat /proc/meminfo
lspci

any of that help or were you looking for something else in particular?

ls -l /proc should help. Anything ending in -info will be useful

---

### Post by OBnascar on 2006-03-21
[QUOTE=macm10]does anyone know what the command is to find out info about proc. and ram in the terminal. i used to know it but i forgot.[/QUOTE]

Give this a try:

'sudo lshw'

---

### Post by oakz on 2006-03-21
If by proc. and ram you mean "processes and their memory usage":

$ top

and if you know the process ID use "ps". See "man ps", there are lots of options for what to show...

---

