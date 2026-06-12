---
title: "Problem: Natty and Virtualbox ctrl+alt+F1"
date: 2011-05-31
forum: General Help
---

### Post by 4Orbs on 2011-05-31
I did an Ubuntu Minimal Install inside a virtual machine on my Xubuntu 11.04 system. Installation went well, as expected. But when it comes time to use Ctrl+Alt+F1 to open a tty login prompt in the virtual machine so I can start installing stuff... the host machine (real desktop) drops to a tty. I did catch a glimpse of the virtual machine going to tty just prior to the host opening into tty, so I know the command is reaching the virtual machine, meaning there is correct keyboard focus. So, how can I stop the host machine from accepting a keyboard command that was meant for the virtual machine?

---

### Post by Toz on 2011-05-31
I believe the key combo is RightCtrl-F1 to switch ttys in a vbox.

---

### Post by 4Orbs on 2011-05-31
Thank you for that, Toz. Guess I should read more and fiddle less. Works like a charm. Problem solved.

---

