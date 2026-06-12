---
title: "where is the plugins directory"
date: 2010-02-23
forum: General Help
---

### Post by dolphinaura on 2010-02-23
Where is the web browser plugin directory?
There used to be one main folder where all browsers would search for the plugins.

---

### Post by jobix on 2010-02-23
Try the .mozilla/plugins directory in your home directory.

---

### Post by lovinglinux on 2010-02-23
> **jobix said:**
> Try the .mozilla/plugins directory in your home directory.

That is the user plugin directory. When you install a plugin from Synaptic, it uses the system folders, so other users and other applications can access it. For instance, flash plugin should be in /usr/lib/mozilla/plugins but there are also several symlinks on other places, like /usr/lib/firefox-addons/plugins, /usr/lib/firefox/plugins, /usr/lib/firefox-3.6/plugins, /usr/lib/xulrunner-addons/plugins, /usr/lib/xulrunner/plugins...

What do you want to do?

---

### Post by dolphinaura on 2010-02-23
> **lovinglinux said:**
> That is the user plugin directory. When you install a plugin from Synaptic, it uses the system folders, so other users and other applications can access it. For instance, flash plugin should be in /usr/lib/mozilla/plugins but there are also several symlinks on other places, like /usr/lib/firefox-addons/plugins, /usr/lib/firefox/plugins, /usr/lib/firefox-3.6/plugins, /usr/lib/xulrunner-addons/plugins, /usr/lib/xulrunner/plugins...

What do you want to do?
Thanks!
ended up adding it to the /usr/lib/mozilla/plugins

I was working on this: [http://ubuntuforums.org/showthread.php?t=1414595](http://ubuntuforums.org/showthread.php?t=1414595)

---

### Post by lovinglinux on 2010-02-23
> **dolphinaura said:**
> Thanks!
ended up adding it to the /usr/lib/mozilla/plugins

I was working on this: [http://ubuntuforums.org/showthread.php?t=1414595](http://ubuntuforums.org/showthread.php?t=1414595)

Interesting. Thanks for sharing.

---

### Post by jobix on 2010-02-23
> **lovinglinux said:**
> That is the user plugin directory. 

You are correct. I misunderstood.

To the OP, just a general comment, but you can use the find command to find directories. For instance, in your case, I might have guessed that the directory is named "plugin" or "plugins" and used:

> find / -name "plugins"

Beware that this could take some time depending on how many files/directories it has to search.

You can tell find to search for directories only and a bunch of other criteria in order to speed it up.

---

