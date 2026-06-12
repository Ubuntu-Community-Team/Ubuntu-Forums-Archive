---
title: "[HELP] I disabled my password on Ubuntu 12.04LTS and there's a problem"
date: 2012-06-11
forum: General Help
---

### Post by Doodling Unity on 2012-06-11
So I disabled my password on Ubuntu, and know everytime I want to install something from Ubuntu Software Center it says *I Need To Authenticate *I type in my old password, it says it failed, and now I can't create an account or change the password or even install something, what should I do???:confused: this is a serious problem!!!:sad:

---

### Post by prshah on 2012-06-11
> **Doodling Unity said:**
> I type in my old password, it says it failed, and now I can't create an account or change

When booting into Ubuntu, tap Left Shift multiple times to bring up the grub menu.

From this menu, select "recovery mode", and subsequently, "root console".

In this console, give the command```
passwd username
``` (replace username with the name of your user).

You will be prompted for a new password. Enter it twice, then exit the console and choose normal boot.

Please post back if you need more assistance.

---

