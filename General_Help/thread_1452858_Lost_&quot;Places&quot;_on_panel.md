---
title: "Lost &quot;Places&quot; on panel"
date: 2010-04-12
forum: General Help
---

### Post by AnotherDave on 2010-04-12
I seem to have lost the Places function on my Gnome panel. 

The files are there, the Places link is there, the Home Folder, Desktop, etc. flyout is there, but the function is kaput.

Any ideas how to get this back?

---

### Post by 2hot6ft2 on 2010-04-12
You can reset the panels to default. Be careful with these commands and start them with sudo. Copy and paste to prevent any typos.
> **lidex said:**
> Terminal:
```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by AnotherDave on 2010-04-12
Thanks! Did as you said, but no luck.

I get the twirlie, which eventually times out. But no files.

---

### Post by AnotherDave on 2010-05-06
I tried upgrading to 10.04 LTS, but it made my system unstable. 

I fixed the problem by backing up /home, reformatting, and installing Debian. Less cruft, much easier to understand!

---

