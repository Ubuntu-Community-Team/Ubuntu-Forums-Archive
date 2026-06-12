---
title: "Flash Player... -_-"
date: 2009-09-15
forum: General Help
---

### Post by ChaosChris2009 on 2009-09-15
Already tried sudo apt-get install flash player

Here's what I got

> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package flash

I can't see to copy to the file manually to /usr/lib/firefox-3.5.2/plugins, Dolphin's denying me access, already checked my authorizations and all, I couldn't that out though

Kubuntu 9.04

Thanks in advance

---

### Post by zvacet on 2009-09-16
Put Firefox 3.5.2 (why not 3.5.3) in your home directory and then copy/paste this commands in terminal

```
if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

---

