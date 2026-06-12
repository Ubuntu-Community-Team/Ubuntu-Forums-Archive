---
title: "&quot;recovery concsole&quot; error with clean and dpkg in 9.10"
date: 2010-01-04
forum: General Help
---

### Post by cong06 on 2010-01-04
I'm working off a clean install of Karmic.

When I hit esc to get the "linux kernel choice" and I go to the recovery console, it brings me the list:
-resume
-clean
-dpkg
-root
-netroot
etc

If I scroll over "clean" or "dpkg", I get a mount error (like mentioned) and I am given a root terminal (all garbled) pressing enter seems to kill the terminal and re-spawn it on the same line so that instead of:
```

root@phaff:#
root@phaff:#

```
I get:
```

root@phaff:#root@phaff:#root@phaff:#root@phaff:#

```
Also certain keystrokes disappear with no hint as to which ones (since enter is the only key that produces visual response). Basically executing commands is potentially possible, but technically impossible. The only  way out is a hard reset.

The temporary solution for me was to use "page down" to skip to the end of the list. It works fine as long as I don't pause over dpkg or clean.

---

