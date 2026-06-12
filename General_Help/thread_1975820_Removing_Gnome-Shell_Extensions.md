---
title: "Removing Gnome-Shell Extensions"
date: 2012-05-07
forum: General Help
---

### Post by airspoon on 2012-05-07
Hello, 
The other day I installed the [system monitor]("https://extensions.gnome.org/extension/120/system-monitor/") gnome-shell extension and because I didn't have lm-sensors installed yet, it gave me an error (in both gnome tweak tool and the extensions.gnome.org website). At least I think that's the reason. 

Anyway, I went and properly installed lm-sensors and ran sensors-detect, so I was hoping that the extension would now work. However,the same little error message in place of the toggle button is preventing me from doing anything with it. I'm assuming that I have to re-install the extension for it to work but I have no idea how to remove it. 

Due to the error, I can't turn the extension on (or off) and instead of the button, I have an error message.

Does anyone know how I can remove it? Can I just delete it from the file system?

Any and all help would be greatly appreciated. Thanks....

---

### Post by markbl on 2012-05-07
Just rm the extension directory from ~/.local/share/gnome-shell/extensions/

BTW, I think the bug you are referring to is the one [I reported recently](https://github.com/paradoxxxzero/gnome-shell-system-monitor-applet/issues/122) to the author. He has fixed it but the new version has/was yet to the pushed to extensions.gnome.org.

---

### Post by airspoon on 2012-05-07
Thanks! I'll remove that directory. Is there an ETA you know of for the update on gnome.org? Have you tried it and it works, or are you waiting on the fix too?

Again, thanks!

---

### Post by airspoon on 2012-05-07
I went and rm the system-monitor directory in the above directory, yet the website still has the annoying error, even though I apparently removed the directory where that extension resides. It's also still showing up in my gnome-tweak tool too.

Could it have left a configuration file somewhere where that website knows which extensions I have? That whole install from a button on a website thing amazes me still and I have no idea how that works.

Thanks.

---

### Post by markbl on 2012-05-07
> **airspoon said:**
> Thanks! I'll remove that directory. Is there an ETA you know of for the update on gnome.org? Have you tried it and it works, or are you waiting on the fix too?

I just git cloned that repo on my machine and added a symlink to the extension into my extensions dir. So I always have the latest version now. The fix he mentions works fine.

---

### Post by markbl on 2012-05-08
> **airspoon said:**
> I went and rm the system-monitor directory in the above directory, yet the website still has the annoying error, even though I apparently removed the directory where that extension resides. It's also still showing up in my gnome-tweak tool too.

No, you just haven't reloaded your gnome-shell session since you removed the dir. Either press Alt+F2 then "r" or just log out and back in.

---

