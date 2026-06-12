---
title: "Menu Bar acting up"
date: 2010-12-04
forum: General Help
---

### Post by VaultTec on 2010-12-04
Need help with this annoying little problem.

To start I use to use Wine but uninstalled it because when ever i clicked on places on the desktop panel and then documents it opened itunes.

Now I get this message when clicking on documents from panel

Could not open location 'file:///home/<user>/Documents'
Failed to execute child process "wine" (No such file or directory)

It does the same for pictures, downloads, etc.
Installing wine does not fix this.
What do?

---

### Post by mc4man on 2010-12-04
see here for 2 ways to fix
[http://ubuntuforums.org/showthread.php?p=10098466#post10098466](http://ubuntuforums.org/showthread.php?p=10098466#post10098466)

**After fixing**, whenever using the 'other application' context menu make sure the 'Remember this application...' option is **unchecked** or the app chosen will become the new default. Applies to both files and folders context menu

---

### Post by VaultTec on 2010-12-04
Thanks for the response.

Its only a problem with the menu on panel and if I r click it gives same message.

I can access documents from places > computer though, its weird.

I would like to recover menu though

---

### Post by mc4man on 2010-12-04
> Its only a problem with the menu on panel and if I r click it gives same message.

Just to make sure it isn't the common issue I linked solution to could you open a terminal, copy and paste this in and post the results?

```
gedit ~/.local/share/applications/mimeapps.list
```

---

### Post by VaultTec on 2010-12-06
Just pops up a window with this message

[Added Associations]
image/jpeg=openoffice.org-draw.desktop;
inode/directory=wine-extension-ipsw.desktop;

---

### Post by VaultTec on 2010-12-07
SOLVED!!!:p

Im a cracker head, your original advice did work

From terminal type "nautilus" > right clicked a folder > open with other application > click on file browser > make sure box is checked with "remember this for all folders > click open > profit!

Thanx a million

---

