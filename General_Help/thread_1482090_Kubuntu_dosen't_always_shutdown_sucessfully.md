---
title: "Kubuntu dosen't always shutdown sucessfully"
date: 2010-05-13
forum: General Help
---

### Post by Falc7 on 2010-05-13
When i try and shutdown the computer, it only actually shuts down about 70% of the time. The remaining 30% it just stays indefinately on the shutting down bootsplash. What can i do? It isen't good for the HDD when i have to hold down the power button

---

### Post by roccivic on 2010-05-13
system -> administration -> log file viewer

See if you find some errors there.

---

### Post by Falc7 on 2010-05-17
I'm using kubuntu, so i used klogs, but the data seems to be cleaned every time i turn off. So the machine stalls on shutdown-> i force turn off-> logs are cleaned. Is there anything else i can try?

---

### Post by Zorael on 2010-05-17
If you disable the boot splash, perhaps the text displayed detailing the shutdown process could tell you what's happening.

To do it once, edit the kernel entry in GRUB2 by hitting Ctrl+E (or perhaps just E?), scroll down to the **linux** line, move to the end of the entry and remove '**splash**'. Then hit Ctrl+X to boot.

To make it a persistent setting, open up **/etc/default/grub** in a text editor, find the line beginning with **GRUB_CMDLINE_LINUX_DEFAULT** and remove the mention of 'splash' from there too, making it look like the following;
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```
Then have GRUB2 reread the file.
```
$ sudo update-grub
```

---

### Post by Falc7 on 2010-05-18
Ah yes i can try that, one other thing i was going to mention is this: if i press ctrl + alt + del (i have set this up so it kills the xserver and logs me out) it shows me a text of what is going on. The last time the machine wouldn't turn off, it was stuck on 'checking batter state' but there was no battery in the laptop at the time.

---

### Post by Falc7 on 2010-05-26
Anyone cure for the 'checking battery state' problem?

---

