---
title: "Drapes Wallpaper management"
date: 2010-05-18
forum: General Help
---

### Post by wired99 on 2010-05-18
**Drapes 0.5.2** does not seem to (fully) work as intended.
I am able to manually change wallpapers with it (but I don't need Drapes to do that).
I wish to [COLOR=green]rotate my wallpaper every time I log-in[/COLOR].

I set the option to **"Switch Wallpaper on Start"** in the [COLOR=blue]options[/COLOR] and it is also included under **"Startup Applications"**, however, it doesn't load when I log into my desktop.

It worked well under Ubuntu 9.04 but didn't quite work under 9.10 and now it does the same under 10.04.

[highlight]Any suggestions?[/highlight]

I'm using Ubuntu 10.04, with Gnome 2.30.0

---

### Post by wired99 on 2010-05-18
I found the answer.

I added the following line to **~/.config/autostart/drapes.desktop** :

```
Type=Application
```saved the file and DONE!!

I found the answer in a bug report:
[https://bugs.launchpad.net/drapes/+bug/292051](https://bugs.launchpad.net/drapes/+bug/292051)

I hope this helps someone else as well.

---

### Post by SKhan on 2010-05-27
i didn't understand it. please tell me in detail. i have same problem.

---

### Post by wired99 on 2010-05-28
Open gedit (or your preferred text program) and then open the following file with it:

home/yourdirectory/.config/autostart/drapes.desktop

(Note the dot [.] in the .config, it's a hidden folder)

add this line at the end of the file: (that's the "drapes.desktop" file)

**Type=Application**

then save.

next time you login it should work.

make sure to set the preferences in Drapes (under "General" tab) so that it starts automatically.

I hope this helps.

---

