---
title: "Adept install problem"
date: 2006-04-04
forum: General Help
---

### Post by shugie on 2006-04-04
I've been using Adept to install packages on KDE. I was trying to install MythTv, but it seems to require postfix. During postfix configuration I canceled and exited. Now Adept lists mailx as Broken and I can't do any installs or uninstalls of anything. It won't let me uninstall it even when I try to uninstall MythTv. How do I fix this?

---

### Post by Neo Ex on 2006-04-04
Well, have you tried to uninstall it via apt-get? (sudo apt-get uninstall mailx).

---

### Post by shugie on 2006-04-04
"sudo apt-get uninstall mailx"

gives me 

"E: Invalid operation uninstall"

---

### Post by Rog131 on 2006-04-04
APT HOWTO:
[http://www.debian.org/doc/manuals/apt-howto/index.en.html](http://www.debian.org/doc/manuals/apt-howto/index.en.html)

3.3 Removing packages
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-remove](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-remove)

"If you no longer want to use a package, you can remove it from your system using APT. To do this just type: apt-get remove package."

Or 

Use synaptic package manager. Synaptic enables you to fix broken packages.

---

### Post by shugie on 2006-04-04
Thank you both very much. The apt-get remove worked.

---

