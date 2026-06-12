---
title: "Ubuntu started too run slow"
date: 2010-01-01
forum: General Help
---

### Post by darthmill on 2010-01-01
My Ubuntu 9.10 has started too run very slow it starts up ok but openin apps and even switchin tabs / type in firefox are very slow and delayed I think it may be due to a bad update what is the best way to find out and run a check on the system. i have disable the fancy desktops but it has not improved it.

Julian

---

### Post by juancarlospaco on 2010-01-01
Bleachbit :)

---

### Post by rudeboyskunk on 2010-01-01
First, what are the specs of your computer?  What programs do you normally have running in the background?  Open up System>Administration>System Monitor, switch to the "Processes" tab, and find which programs are using the most memory and %CPU.  When you disabled special effects, did you go to System>Preferences>Appearance and then click on the "Visual Effects" tab, and then choose "None"?  What web browser do you normally run?  If you're using Firefox, try Chrome, it's much faster.  Doing sudo apt-get update && sudo apt-get dist-upgrade in a terminal should update you to the latest everything as well.

---

### Post by darthmill on 2010-01-01
Too late it`s got worse will not boot now runs a check disk and freezes. looks like a reinstall.

---

### Post by plapczynski on 2010-01-01
You might want to check your HDD.  With newer PCs there is an option in the 
bios to do this,

---

