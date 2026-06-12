---
title: "WINE problem"
date: 2006-02-12
forum: General Help
---

### Post by Disastorm on 2006-02-12
when i try to run wine on a file it says some errors about ReplaceIcon no color, and then it says
Application tries to create a window, but no driver could be loaded. Make sure that your X server is running and that $DISPLAY is set correctly.  It seems to be able to create a window for winecfg though.

*nm it seems to work now that i type in sudo wine <whole address> rather than going to the directory and just typine wine <filename>*

---

### Post by dcstar on 2006-02-12
[QUOTE=Disastorm]when i try to run wine on a file it says some errors about ReplaceIcon no color, and then it says
Application tries to create a window, but no driver could be loaded. Make sure that your X server is running and that $DISPLAY is set correctly.  It seems to be able to create a window for winecfg though.

*nm it seems to work now that i type in sudo wine <whole address> rather than going to the directory and just typine wine <filename>*[/QUOTE]
Wine is not supposed to run as sudo, if you have been using sudo then you wine setup may not be right.

---

