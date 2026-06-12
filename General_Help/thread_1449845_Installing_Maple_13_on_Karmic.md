---
title: "Installing Maple 13 on Karmic"
date: 2010-04-08
forum: General Help
---

### Post by J_Winnfield on 2010-04-08
hi everyone,

i have a problem to install maple 13 on my karmic ubuntu system. i got a file named maple13Linux32Installer.bin that i still can't execute. java and the stdlibc++ is already installed. i set chmod 755 and when i enter ./Maple13Linux32Installer.bin in the terminal, it still says, that the file can't be executed...
thanks to anyone how can give me a hint...
Jules

p.s. excuse my english, i'm from germany...

---

### Post by gadolinio on 2010-04-08
> **J_Winnfield said:**
> hi everyone,

i have a problem to install maple 13 on my karmic ubuntu system. i got a file named maple13Linux32Installer.bin that i still can't execute. java and the stdlibc++ is already installed. i set chmod 755 and when i enter ./Maple13Linux32Installer.bin in the terminal, it still says, that the file can't be executed...
thanks to anyone how can give me a hint...
Jules

p.s. excuse my english, i'm from germany...

Just to make sure, right-click the bin file, go to properties, then permissions tab. Check that the "allow executions as a program" (or stg like that) box is ticked.
Open a terminal, type "cd /PATH_TO_THE_BIN_FILE", hit enter. Then type "sudo Maple13Linux32Installer.bin", and hit enter. It will ask for your password; provide it and follow instructions. Does sudo make a difference?

---

### Post by J_Winnfield on 2010-04-08
thank you for your reply...the .bin file is marked to execute as a program...and the funniest thing is, a few month ago i installed it and it worked. i remenber that i even got problems like these now, but i don't remember the solution ](*,)
sudo does not have any effect, i tryed with sudo -s and with a simple sudo before the ./filename.bin. i even tryded to install it with the console option, a hint from maplesoft, but no effect at all. also the file can't be broken, i made "safty-copy" and it doesen't work with a fresh copy...the problem is, i'm studying mathmatics and i need my maple...

---

