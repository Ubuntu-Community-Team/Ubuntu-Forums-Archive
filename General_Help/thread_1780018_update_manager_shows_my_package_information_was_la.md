---
title: "update manager shows my package information was last updated 34 days ago?"
date: 2011-06-11
forum: General Help
---

### Post by mirchichamu on 2011-06-11
what does that means? I have a yellow rectangle on the panel, when I click it says your system is up to date...also says the update information is outdated...how to fix that?

---

### Post by Frogs Hair on 2011-06-11
Run this code in the terminal and open the update manager and see if there are updates to install. The command will reload your package information . ```
sudo apt-get update
```

---

### Post by mirchichamu on 2011-06-11
> **Frogs Hair said:**
> Run this code in the terminal and open the update manager and see if there are updates to install. The command will reload your package information . ```
sudo apt-get update
```

Thanks Frogs Hair for your cooperation. I did it but still the same..I got a message that some repositories could not be fetched. SCREENSHOT IS INCLUDED.

---

### Post by philinux on 2011-06-11
> **mirchichamu said:**
> Thanks Frogs Hair for your cooperation. I did it but still the same..I got a message that some repositories could not be fetched. SCREENSHOT IS INCLUDED.

[http://ubuntuforums.org/showthread.php?t=1221323](http://ubuntuforums.org/showthread.php?t=1221323)
This post shows how to fix the gpg key errors.

---

### Post by mirchichamu on 2011-06-11
> **philinux said:**
> [http://ubuntuforums.org/showthread.php?t=1221323](http://ubuntuforums.org/showthread.php?t=1221323)
This post shows how to fix the gpg key errors.

Thanks a million philinux for your concern.
My other keys were corrected by the tutorial but this one not [W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404  Not Found]
....so my update manager still says that the package information is 34 days old.

I would be extremely grateful for further help.

---

### Post by philinux on 2011-06-11
> **mirchichamu said:**
> Thanks a million philinux for your concern.
My other keys were corrected by the tutorial but this one not [W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404  Not Found]
....so my update manager still says that the package information is 34 days old.

I would be extremely grateful for further help.

I guess you need to remove that entry from your sources list.

```
gksudo gedit /etc/apt/sources.list
```

Or use synaptic or software center to edit the list.

---

### Post by mirchichamu on 2011-06-11
> **philinux said:**
> I guess you need to remove that entry from your sources list.

```
gksudo gedit /etc/apt/sources.list
```

Or use synaptic or software center to edit the list.

Thanks 10 millions times. It solved the problem. I removed the entry in software sources and now everything is fine. Bravo.

---

