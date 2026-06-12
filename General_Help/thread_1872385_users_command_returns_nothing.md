---
title: "users command returns nothing"
date: 2011-10-30
forum: General Help
---

### Post by imbjr on 2011-10-30
Unless I log in via Ctrl+Alt F1, I get an empty users list via the command line.

Anyone know why?

---

### Post by Toz on 2011-10-30
I think this might be related to a bug report I made a short while back ([https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297")). who, w, and last don't show any graphical logins, only tty logins. According to the bug report, its been fixed in the next version.

---

### Post by imbjr on 2011-10-31
> **Toz said:**
> I think this might be related to a bug report I made a short while back ([https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297")). who, w, and last don't show any graphical logins, only tty logins. According to the bug report, its been fixed in the next version.

I also found this bug that seems to fit the bill:

[https://bugs.launchpad.net/ubuntu/+source/vte/+bug/864609](https://bugs.launchpad.net/ubuntu/+source/vte/+bug/864609)

---

### Post by gsmanners on 2011-10-31
Interesting. Yeah, I've noticed that if I use xfce-terminal, it exhibits that problem. But, if I use xterm, the users command seems to be functioning.

---

