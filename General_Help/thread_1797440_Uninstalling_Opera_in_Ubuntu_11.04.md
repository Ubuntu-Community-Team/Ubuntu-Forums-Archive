---
title: "Uninstalling Opera in Ubuntu 11.04"
date: 2011-07-05
forum: General Help
---

### Post by zemadz on 2011-07-05
Hi,

I have a problem with Opera 11.10. I can't seem to uninstall it. There is no package related to it in Synaptics Package Manager. It isn't listed in the Software Center.

When I search for "opera" in Unity search it shows up and I can launch it. The launch command is "application://opera-browser.desktop/." but there is no file like that in /usr/share/applications folder.

Need help with removing this, it's making me crazy.

Also, when I install Opera 11.50, then it installs separately and still launches 11.10 from the Unity search.

---

### Post by An Sanct on 2011-07-05
This will remove Opera

```
sudo apt-get update && sudo apt-get remove opera
```

After that, install it from the software center or [opera.com]("http://www.opera.com/browser/download/").

---

### Post by zemadz on 2011-07-05
> **An Sanct said:**
> This will remove Opera

```
sudo apt-get update && sudo apt-get remove opera
```

After that, install it from the software center or [opera.com]("http://www.opera.com/browser/download/").

There is no Opera in the Package Manager list so it won't update it. It says: "Package opera is not installed, so not removed"

---

### Post by zemadz on 2011-07-05
Ahh, found the solution. Opened System Monitor, where I investigated "Memory Maps" of Opera process. Found out that it was installed in /home/user/.local/opera folder.

Didn't think that home folder doesn't search hidden files even after you've selected to show them.

Anyway, thanks for trying An Sanct.

---

### Post by An Sanct on 2011-07-05
'yer welcome ;)

---

