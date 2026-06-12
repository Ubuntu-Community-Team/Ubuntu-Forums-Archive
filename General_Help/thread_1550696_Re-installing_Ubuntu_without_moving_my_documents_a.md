---
title: "Re-installing Ubuntu without moving my documents and changing my settings"
date: 2010-08-11
forum: General Help
---

### Post by iguanaboy on 2010-08-11
Hello, I want to re-install my 10.04 because Anthy (app to write in Japanese) won't work any more, whatever I try; how do I proceed? I'd like to find a way to keep my files/Firefox settings and bookmarks etc. intact during the re-install, just like I upgraded from Koala to Lynx. Is that possible? If so, how do I do it?

Sorry if it's a n00bish question BTW

---

### Post by jakupl on 2010-08-11
Back up your /home to a usb thumb drive, and restore it after the reinstall.

---

### Post by jakupl on 2010-08-11
remember that the configuration files in /home are hidden, so you need to do ctrl + h in order to see them and copy them.

---

### Post by Vaphell on 2010-08-11
setting up separate /home partition makes reinstall much less painful. root partition with core system files is always wiped out during reinstallation but you can leave separate /home untouched, so when you log in for the first time all your stuff and configs are there right off the bat.

---

### Post by iguanaboy on 2010-08-12
Setting up a separate /home partition sounds good since I don't have an extra hard-disk with me atm; how do you do that?

---

