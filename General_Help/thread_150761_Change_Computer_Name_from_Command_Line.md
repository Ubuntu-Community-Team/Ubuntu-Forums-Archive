---
title: "Change Computer Name from Command Line?"
date: 2006-03-26
forum: General Help
---

### Post by jj1814 on 2006-03-26
Can someone tell me how to change my computer name from the command line? Every HowTo I find discusses the methods for doing it through the Network GUI tool. However, I cannot successfully log in as Administrator via the GUI. I put in the password, but none of the buttons are enabled after I give the password. I know that the password is correct because it's one of my typical passwords, and this is the same password I use for all sudo commands via the command line.

---

### Post by colo on 2006-03-26
You need to adjust /etc/hostname and /etc/hosts to your needs. Should be self-explanatory once you're editing the files.

---

### Post by jj1814 on 2006-03-26
Ok....I have edited the files accordingly. I assume a reboot is needed to reflect the changes, so *BRB*

*crossing fingers*

---

