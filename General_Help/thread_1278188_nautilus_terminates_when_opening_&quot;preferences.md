---
title: "nautilus terminates when opening &quot;preferences&quot;"
date: 2009-09-29
forum: General Help
---

### Post by khaledkammar on 2009-09-29
Nautilus crashes each time i try to open "EDIT--> Preferences" !

I tried re-installation but problem presists. Is there any way to fix it?

---

### Post by Giblet5 on 2009-09-29
It appears to be a bug (422282) in Nautilus.

Here's the [launchpad info]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/422282").

("nautilus crash preferences" in Google returns 583K hits)

I tend to use Krusader.

---

### Post by Elcid247 on 2009-09-29
did u try doing it with complete removal?

```
sudo apt-get purge nautilus
```

if that doesnt work u could delete the .gconf/apps/nautilus folder manually

then press alt+ F2 (to bring up run) and issue

```
pkill nautilus
```

then alt + F2 again and issue

```
nautilus
```

---

### Post by StuartN on 2009-09-29
> **Elcid247 said:**
> ```
nautilus
```

That is the important bit - if a command behaves strangely, then launch it in a terminal because you will see the error messages sent to stderr. If you launch it from the desktop then all those messages are hidden.

---

