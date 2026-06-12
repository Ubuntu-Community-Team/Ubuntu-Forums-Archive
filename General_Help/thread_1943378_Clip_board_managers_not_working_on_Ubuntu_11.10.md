---
title: "Clip board managers not working on Ubuntu 11.10"
date: 2012-03-19
forum: General Help
---

### Post by psarin on 2012-03-19
Hi,

I recently moved to Ubuntu(Ubuntu 11.10). Immediately after the installation i tried installing clipit clipboard manager and it worked for a while. Later, may be after a software upgrade or so, it's no longer pasting the entry when i try to.

When i copy, it shows up in the list, but pasting to an application doesn't work. I am using clipit 1.4.1

I tried installing pastie, and see the same issue.

Requesting for help..

Thanks

---

### Post by Habitual on 2012-03-19
parcellite in a repo near you. :)

---

### Post by psarin on 2012-03-19
I tried parcellite too..but same behaviour.

I think its an ubuntu related (clip board?) issue since none of them are working.

I also tried these apps using Unity and Gnome 3 shell..same behavior :(

Please help!

---

### Post by stinkeye on 2012-03-20
Does ctrl+v paste the clipboard contents. (ctrl+shift+v if in terminal)

One thing you could check is 
```
gsettings get org.gnome.settings-daemon.plugins.clipboard active
```

> Description: Whether this plugin would be activated by gnome-settings-daemon or not

---

### Post by psarin on 2012-03-20
gsettings get org.gnome.settings-daemon.plugins.clipboard active
true


This is showing as "true"

---

