---
title: "Logon GUI not loading"
date: 2010-12-25
forum: General Help
---

### Post by Pataforce8 on 2010-12-25
Hello all

I recently decided to get back into Ubuntu and installed 10.10 on my Acer Aspire 7741Z. The live USB worked great but the installed OS won't load the GUI. The loading screen does not show but instead there is a ton of text. The logon is the 'standard' logon (Ubuntu 10.10 -computer name- tty1). I can logon using the account information that the graphical installation asked for. After awhile, the screen goes blank. Pressing the power button, the text comes back and Ubuntu the message "ppdev: user-space parallel port driver" has appeared. Using "startx" causes the screen to go blank, and the screen comes back when the power button is pressed before shutting down.

Many thanks in advance!

---

### Post by Pataforce8 on 2010-12-26
Ahh I got it fixed.

I started ubuntu in recovery mode, and then started the failsafex. That allowed me to download all the updates which fixed my problem.

---

### Post by quantumrider on 2010-12-29
I'm also having exact same problem... how do I start it in recovery mode? when I boot it from the hard drive after installation it just goes to command prompt and asks me to login...

---

### Post by Pataforce8 on 2010-12-29
On the grub menu select the linux kernel that reads 'Recovery Mode' after it. If the grub menu is not showing up during boot, hold the right shift button.

---

