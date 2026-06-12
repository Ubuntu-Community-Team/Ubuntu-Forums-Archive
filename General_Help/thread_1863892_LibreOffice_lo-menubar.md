---
title: "LibreOffice: lo-menubar"
date: 2011-10-18
forum: General Help
---

### Post by vasa1 on 2011-10-18
Anyone using it in 11.10? Could you share your experience?

The Software Center mentions **28** reviews but only **three** are visible despite clicking on "Check for more reviews".

Edit:
I installed it but I am not 100% happy because I like to use Alt+Window, New to open a new window for the same document. But that is not an option in the "global menu".

I don't know how to uninstall it. When I look in Alt+Tools, Extension Manager, I see three extensions listed:
Copy Visible cells (which I had installed on LibreOffice 3.3 / Natty)
menubar (installed via Ubuntu Software Center)
Script Provider for Python 3.3.0 (which seems to have been there by default since I didn't install it)

The last two, menubar and Script Provider have little locks next to them.

While the first, "Copy visible cells" has a disable/remove option, the two with locks next to them don't. So it looks like I cannot disable or remove menubar unless someone helps me!

---

### Post by vasa1 on 2011-10-18
I also posted over at [http://nabble.documentfoundation.org/](http://nabble.documentfoundation.org/) and read a few related posts.

It seems that the current way to remove pad-locked extensions is by just deleting them from the command line or via the file manager.

So, with LibreOffice not running, I deleted /usr/lib/libreoffice/share/extensions/menubar and I've now got back the original behavior. I had to go into admin mode for that. I guess if there were a way to install it as user, I may have been able to remove it using LibreOffice's Extension Manager.

---

### Post by ubu_dynamite on 2011-10-18
Probably better to just remove it instead of deleting the file
```
sudo apt-get remove lo-menubar
```

---

### Post by vasa1 on 2011-10-18
> **ubu_dynamite said:**
> Probably better to just remove it instead of deleting the file
```
sudo apt-get remove lo-menubar
```

Thanks!
```
...:~$ sudo apt-get remove lo-menubar
[sudo] password for ...: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  lo-menubar
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 168 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 155277 files and directories currently installed.)
Removing lo-menubar ...
Processing triggers for libreoffice-common ...
Synchronizing repository for bundled extensions
 Disabling: menubar
  Disabling: Jobs.xcu
  Disabling: menubar.uno.so
 



unopkg done.

```

---

