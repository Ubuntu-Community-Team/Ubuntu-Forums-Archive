---
title: "Install Gnome from terminal"
date: 2006-04-21
forum: General Help
---

### Post by vulpeso on 2006-04-21
I removed and re-added the alsa and alsa-util packages using package manager in troubleshooting an audio issue. Gnome desktop was removed with alsa, but I did not think to reinstall it before rebooting. Now when I boot into Breezy, I have only the command shell. I need to know how to re-install the desktop. Or, is there any way to re-install the OS without trashing my data? This would be preferable as it may solve my audio issue too.

---

### Post by xXx 0wn3d xXx on 2006-04-21
[QUOTE=vulpeso]I removed and re-added the alsa and alsa-util packages using package manager in troubleshooting an audio issue. Gnome desktop was removed with alsa, but I did not think to reinstall it before rebooting. Now when I boot into Breezy, I have only the command shell. I need to know how to re-install the desktop. Or, is there any way to re-install the OS without trashing my data? This would be preferable as it may solve my audio issue too.[/QUOTE]
> sudo apt-get install ubuntu-desktop

You may loose some of your settings but your data will still be there.

---

### Post by vulpeso on 2006-04-21
Many thanks. Easy as pie when you know the correct command.

Now if I get the sound to work...

---

### Post by xXx 0wn3d xXx on 2006-04-21
[QUOTE=vulpeso]Many thanks. Easy as pie when you know the correct command.

Now if I get the sound to work...[/QUOTE]
Ok, glad that's fixed. Now try to get sound to work, type "sudo alsamixer" in terminal (no quotes) and make sure nothing is muted or disabled.

---

