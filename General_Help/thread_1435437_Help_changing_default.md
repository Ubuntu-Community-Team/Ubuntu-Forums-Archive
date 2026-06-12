---
title: "Help changing default"
date: 2010-03-21
forum: General Help
---

### Post by Colo2 on 2010-03-21
Hello
I'm an ubuntu user, so by default I am using Nautilus. However, I tend to prefer Dolphin which I also have on my system.
How would I go about changing the default file manager to dolphin, (so that all my folders open with dolphin as opposed to nautilus)

Thanks :)


Tom

---

### Post by Colo2 on 2010-03-21
No one knows? :(

---

### Post by Colo2 on 2010-03-21
nevermind, worked it out myself

---

### Post by Usabent on 2010-03-21
Wow that was fast...

---

### Post by Colo2 on 2010-03-21
Yeah..

I uninstalled Nautilus and all the links in the "Places" menu open with Dolphin now. However folders from the desktop open with something called "File Browser"
I can't work out how to change that :( what is it? how do I get rid of it?

---

### Post by howefield on 2010-03-21
> **Colo2 said:**
> How would I go about changing the default file manager to dolphin, (so that all my folders open with dolphin as opposed to nautilus)


This seems to work.

Edit the following file

/usr/share/applications/nautilus-folder-handler.desktop 

and change nautilus --no-desktop %U to dolphin.

Terminal command.

```
gksudo gedit /usr/share/applications/nautilus-folder-handler.desktop
```

You might want to make a backup of the file before editing.

---

