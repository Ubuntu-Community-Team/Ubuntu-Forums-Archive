---
title: "How to completely uninstall Google Chrome"
date: 2011-05-22
forum: General Help
---

### Post by TMachado on 2011-05-22
I need to reinstall Chrome (v11 - google-chrome-stable)

I tried sudo apt-get remove --purge ....

second try I used synaptic manager and market "completely removal". Also I deleted the chrome folder on .cache.

Problem is, when I install again it comes will all my preferences (extensions, theme, sync). I need to have chrome like I just installed my ubuntu.

How can I do that?

---

### Post by gandaran on 2011-05-22
look for the chrome user profile in the hidden /home/user and delete all chrome folders there

---

### Post by TMachado on 2011-05-22
> **gandaran said:**
> look for the chrome user profile in the hidden /home/user and delete all chrome folders there

Well that I already know :)

I eventually found the folder I needed to delete at .config.

---

### Post by cbowman57 on 2011-05-22
> **TMachado said:**
> Well that I already know :)

I eventually found the folder I needed to delete at .config.

Bingo!  Glad you already located it.

---

