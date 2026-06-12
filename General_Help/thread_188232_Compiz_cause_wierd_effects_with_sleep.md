---
title: "Compiz cause wierd effects with sleep"
date: 2006-06-03
forum: General Help
---

### Post by olsonar on 2006-06-03
i use aiglx/compiz on gnome, and if compiz is running when i put my computer to sleep, it doesn't resume correctly. i either get an error about the DRI driver and have to force shutdown, or the GUI stops rendering properly and i have to log out/in. with compiz turned off, sleep works fine. is there a way to fix this? or, failing that, to make compiz turn off before the computer goes to sleep and turn back on when it resumes?

---

### Post by givré on 2006-06-03
Sleep or hibernate will not run with compiz at this stage of it developement (i hope it will work one day). You have to switch to metacity before. two way:

- if you have install gset-compiz it is as simple as clicking on the icone and switch to metacity
- if you don't have gset-compiz, type alt-F2 and launch metacity --replace

You will know be able to suspend

---

### Post by olsonar on 2006-06-03
yeah, i have the icon. but is there a way to do it automatically? like adding something to my /etc/acpi/sleep.sh file?

---

### Post by givré on 2006-06-04
There is a script call /etc/acpi/prepare.sh which is execute when you sleep your cumputer. I try to had metacity --replace at the beginning of this scipt, but it was not working as well as expected, sometimes it works, sometimes no, and i don't really why.
So i remove this line and i decide to do it manualy.
but when you pass one second to click on *sleep*, you could pass an other second to click on *switch to metacity* ;)

---

### Post by olsonar on 2006-06-04
the reason i want it to happen auto matically is because i have a *laptop*. When i'm on battery, i want to be able to close the the lid and have it sleep without needing to worry about whether it'll come back. I'll try adding metacity --replace, see if it works better for me. if that works, then what command could i add to start compiz afterward?

---

### Post by s|k on 2006-06-04
I still haven't got compiz to work at all yet.

---

### Post by olsonar on 2006-06-04
adding it didn't work. any ideas? at all? i really like compiz, but if i can't sleep i'll have to stop using it.

---

