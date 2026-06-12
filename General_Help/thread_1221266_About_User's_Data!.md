---
title: "About User's Data!"
date: 2009-07-23
forum: General Help
---

### Post by ayonkhan on 2009-07-23
Where does the following application store user's data in Linux Mint 7?
[list][*] Synaptic
[*] Nautilus
[*] VLC Media Player
[*] Banshee Media Player[/list]
I can't find anything like .synaptic, .vlc . . . in home directory. :(

---

### Post by mcduck on 2009-07-23
Synaptic runs as root, so it definitely won't save any settings in your user's home directory.

For the rest, check directories like ~/.config and ~/.local/share.

Also at least Nautilus uses gconf, so it's setting files would be in .gconf, and if you need to edit the settings you might want to use gconf-editor instead of directly editing the text files..

---

### Post by spiderbatdad on 2009-07-23
check out /usr/share
also use ```
locate <program or file>
```

---

