---
title: "A command to show tree size information?"
date: 2010-04-24
forum: General Help
---

### Post by HHx66 on 2010-04-24
I'm trying to find a command or program to show what files and folders are taking up the most space on the hard drive, much like tree size view on windows, is there and equivalent on linux?

---

### Post by TitanusEramius on 2010-04-24
I don't think it's quite the same, but the command "du" is working good if you gives the right input:

du -h /home
du -m /home

You can read the manual with man:

man du

---

### Post by HHx66 on 2010-04-24
That works. Thanks for the information!

---

