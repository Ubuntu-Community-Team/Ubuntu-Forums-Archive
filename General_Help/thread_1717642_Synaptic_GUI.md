---
title: "Synaptic GUI"
date: 2011-03-30
forum: General Help
---

### Post by Donald A Thomson on 2011-03-30
I installed Netbeans using the Synaptic GUI and it worked ok. Netbeans is now corrupted. I used the Synaptic GUI to completely remove it. That worked. I used the Synaptic GUI to download it again. It claimed to do it in 2 seconds and it is back to my corrupted Netbeans and practice projects. Obviously an efficiency move to reduce downloads because it was already archived somewhere by Synaptic.

How can I make the Synaptic GUI really download all of Netbeans again?  I am not going to attempt to solve Netbeans mysteries.

If there is no easy way to make the Synaptic GUI download, I will reinstall Wndows XP and my software for it, bring them up to date and reinstall Ubuntu 10.10 on another partition, bring it up to date and reinstall Netbeans. The only advantage of that method is that it works.

---

### Post by mikewhatever on 2011-03-30
You can delete the cached packages from Synaptic: Settings->Preferences, Files tab, 'Delete Cached Files'.

---

### Post by nothingspecial on 2011-03-30
Everything downloaded is kept in /var/cache/apt/archives

It saves you having to download it again. Find it there and delete it. The trouble is, what you download is going to be exactly the same as what you've just deleted.

The corruption is more likelyy to be in a config file somewhere.

---

### Post by Enigmapond on 2011-03-30
If you open the terminal and do:

```
sudo apt-get purge netbeans
```

This will uninstall and delete the config file.

---

