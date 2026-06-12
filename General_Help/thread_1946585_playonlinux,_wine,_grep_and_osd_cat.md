---
title: "playonlinux, wine, grep and osd_cat"
date: 2012-03-25
forum: General Help
---

### Post by Jagoly on 2012-03-25
Hi. I'm trying to modify my playonlinux oblivion launcher to show a pretty FPS overlay.

Based of of a command on a forum post on the wine forums ([http://forum.winehq.org/viewtopic.php?p=62434]("http://forum.winehq.org/viewtopic.php?p=62434")), I've modified my launcher to this:
```
#!/bin/bash
[ "$PLAYONLINUX" = "" ] && exit 0
source "$PLAYONLINUX/lib/sources"
export WINEPREFIX="/home/jagoly/.PlayOnLinux/wineprefix/TheElderScrolls4_Oblivion"
export WINEDEBUG="fps"
cd "/home/jagoly/.PlayOnLinux/wineprefix/TheElderScrolls4_Oblivion/drive_c/./Program Files/Bethesda Softworks/Oblivion"
POL_Wine obse_loader.exe 2>&1 | tee /dev/stderr | grep --line-buffered "trace:fps:swap" | osd_cat
```
Which works well. However, it looks rather ugly and is difficult to read (see screenshot). So I'm trying to make it nicer.

What I'm stuck on is limiting it to just the **.**fps part.

If I try to pipe grep's output first through "cut -c 50-57" then it will not work. I think this is just me being a n00b, not knowing what "--line-buffered" does. If I try to put the cut output into another file (I tried ~/.polfps), and then pipe that to osd_cat then it doesn't work, because the file (~/.polfps) doesn't get modified until oblivion closes (when it does, osd_cat actually does show for one cycle).

I'm not a super n00b, but my knowledge is more of using an interactive shell, eg on my server, then actually writing scripts :-(

If anyone can point me in the right direction, I'd greatly appreciate it :-)

---

### Post by jayshomebrew on 2012-03-25
I can't see exactly what field you're trying to get, if its the 5th one, then you can pipe it thru awk:

so if you had text file foo.bar that looked like this:
mary jane joe rick fps jenny

```
cat foo.bar| awk '{print $5}'
```
would output "fps"


so this might work for you:
```
POL_Wine obse_loader.exe 2>&1 | tee /dev/stderr | grep --line-buffered "trace:fps:swap" | awk '{print $5}'| osd_cat
```

---

