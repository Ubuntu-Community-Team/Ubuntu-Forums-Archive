---
title: "Cannot copy password into pinentry window with GPG"
date: 2011-01-11
forum: General Help
---

### Post by Rytron on 2011-01-11
Hi.

How do I enter password via terminal? I tried gpg in Linux Mint 10.10 vdi and it took my password via the terminal and I could paste a long password in. I tried 'Shift + Insert'; 'Ctrl + v' and a virtual keyboard.

Is it a program I installed in Ubuntu that forces me to use the pinentry window instead of the terminal?

Thanks.

---

### Post by mikewhatever on 2011-01-11
Use ctrl+shift+v to paste in a terminal.

---

### Post by Rytron on 2011-01-14
> **mikewhatever said:**
> Use ctrl+shift+v to paste in a terminal.

Thanks but I cannot do that as the pinentry window is open.

---

### Post by Rytron on 2013-01-01
A way around this is to just use the [COLOR="Magenta"]pinentry-curses[/COLOR] package and remove [COLOR="Red"]pinentry-qt4[/COLOR] + [COLOR="Red"]pinentry-gtk2[/COLOR].

---

