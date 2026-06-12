---
title: "Trouble finding package libgtk-1.2.so.0"
date: 2006-06-09
forum: General Help
---

### Post by Michael Powers on 2006-06-09
I am trying to install and use win4linpro on a intel box. Am getting to following message in the terminal

/opt/win4linpro/bin/mergepro-gfx: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

win4lin troubleshooting guide documents this message and tells me to install this package in my system. I can find similarly named packages but not specifically libgtk-1.2so.0. The similar package that i found i think that it was libgtk-1.2.0 did not solve the problem.

Any suggestions?

---

### Post by Ramses de Norre on 2006-06-09
Install libgtk1.2-common, the one you installed is specially for the gimp.

---

### Post by Michael Powers on 2006-06-09
I just read your message and installed libgtk1.2-common. The synaptic Package Manager said that it was already installed. I marked it for reinstallation. Reinstalled and rebooted. Went to run win4lin and got the same terminal message as before. Any further suggestions?

---

### Post by Michael Powers on 2006-06-09
found package libgtk-1.2 "Not the common" and it worked. Thanks for your help.

---

