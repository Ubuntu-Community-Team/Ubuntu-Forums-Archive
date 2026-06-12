---
title: "Getting cupsys-common error when I try to print using Adobe Reader on ubuntu"
date: 2011-07-13
forum: General Help
---

### Post by byronforum24 on 2011-07-13
can anyone please help me, this is quite urgent, I can print through my samsung printer on ubuntu and everything through the network, but whenever I try to print through the network using Adobe Reader I get a Package cupsys-common error, can anyone tell me how to fix this asap pls???

---

### Post by dino99 on 2011-07-13
CUPS-PDF provides a PDF Writer backend to CUPS. This can be used as a
virtual printer in a paperless network or to perform testing on CUPS.

Documents are written to a configurable directory (by default to ~/PDF)
or can be further manipulated by a post-processing command.

Alternative: xpdf

---

### Post by Neovos on 2012-06-29
This problem still exists. Other programs print just fine and using lpr from the terminal works. I have a Samsung printer, so I eventually fingured out I could just bypassed my printers custom "lpr" program thing located at /opt/Samsung/mfp/bin/slpr by symlinking it straight to the system lpr. This worked for me and has regained my ability to print from Adobe.

```
sudo mv /opt/Samsung/mfp/bin/slpr /opt/Samsung/mfp/bin/slpr.old
sudo ln -s /usr/bin/lpr /opt/Samsung/mfp/bin/slpr
```

You might have to change some things around depending on your printer but hopefully this helps someone.

---

### Post by Neovos on 2012-10-03
Update: I saw that the software updater updated my Samsung drivers again yesterday, predictably, this same thing broke and I used the same fix I listed above to fix it. Amazing.

---

### Post by Neovos on 2013-05-10
Update: same update, same problem, same fix, still amazing.

---

