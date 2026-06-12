---
title: "Uninstalling a manually installed package..."
date: 2010-09-08
forum: General Help
---

### Post by DeadlyOats on 2010-09-08
I downloaded vuze_Installer.tar.bz2 from the Vuze website.  I then unpacked the contents into usr/local/bin.  I want to un-install it now.  I tried using Synaptic Package Manager, but vuze is not shown as installed.

So, I went to usr/local/bin, and was going to "Move to Trash", but root owns the file and all of its contents.

If I do this in a terminal, [COLOR="Red"]**sudo chmod o+w usr/local/bin/vuze**[/COLOR] to the vuze folder in usr/local/bin, will I be able to "Move to Trash" the vuze folder and all of its contents, or do I have to do it to each item within the folder?

Or is this the wrong way to go about it?  Since I din't install vuze via Synaptic Package Manager, I have to manually remove vuze.  If what I suggested, above, is the wrong way, how do I do it correctly?

---

### Post by wojox on 2010-09-08
Why don't you just use sudo to remove it?

```
sudo rm -rf /usr/local/bin/vuze
```

---

### Post by dirghrabadia on 2010-09-08
```

sudo apt-get purge *applicationname*

```

---

### Post by Elfy on 2010-09-08
[http://ubuntuforums.org/showpost.php?p=5327769&postcount=3](http://ubuntuforums.org/showpost.php?p=5327769&postcount=3)

It seems ...

---

### Post by Elfy on 2010-09-08
> **dirghrabadia said:**
> ```

sudo apt-get purge *applicationname*

```

Won't work for an app installed from a tarball

---

### Post by mikewhatever on 2010-09-08
Anything you install from a deb package should be removable from Synaptic. Vuze is obviously not that case, so that you just have to delete the directory you'd unpacked it to. As wojox suggests above,

sudo rm -r /usr/local/bin/vuze

---

### Post by DeadlyOats on 2010-09-08
Thank you wojox and mikewhatever.

[COLOR="Red"]**sudo rm -r /usr/local/bin/vuze**[/COLOR] got rid of it lickety-split!

---

