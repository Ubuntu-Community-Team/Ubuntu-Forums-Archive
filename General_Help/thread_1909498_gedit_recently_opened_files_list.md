---
title: "gedit recently opened files list"
date: 2012-01-15
forum: General Help
---

### Post by vasa1 on 2012-01-15
The default is 5. I'd like to increase it. The solution given [here]("http://ubuntuforums.org/showpost.php?p=7013335&postcount=2") apparently doesn't apply: under ui, there's no "recents". Plus gedit is now at version 3.2.3 and what I can see when I run ```
gconf-editor
``` and navigate to **/apps** is **gedit-2**.

---

### Post by dino99 on 2012-01-15
dont know where you can change it.

[https://help.ubuntu.com/community/gedit](https://help.ubuntu.com/community/gedit)

---

### Post by vasa1 on 2012-01-15
It's quite straight-forward in Geany. Oh, well!

---

### Post by Vaphell on 2012-01-15
in oneiric try this:
**d**conf-editor
org > gnome > gedit > preferences > ui > max-recents

---

### Post by bluexrider on 2012-01-15
> **vasa1 said:**
> The default is 5. I'd like to increase it. The solution given [here]("http://ubuntuforums.org/showpost.php?p=7013335&postcount=2") apparently doesn't apply: under ui, there's no "recents". Plus gedit is now at version 3.2.3 and what I can see when I run ```
gconf-editor
``` and navigate to **/apps** is **gedit-2**.
I don't know where you are getting the information but I can set the preferences using the gconf-editor  I have 2.30.4 installed

Are you sure you opened the last setting (drop down) I found mine?

---

### Post by vasa1 on 2012-01-15
> **Vaphell said:**
> in oneiric try this:
**d**conf-editor
org > gnome > gedit > preferences > ui > max-recents

Thank you! I installed the **d** and it did the job!

bluexrider, my gedit is a later version (3.2.3) than the one you mention (2.30.4).

Marking as [solved].

---

### Post by vasa1 on 2012-01-15
bluexrider, you may also like to read [this]("http://askubuntu.com/questions/91403/when-to-use-gconf-vs-dconf"). It explains a bit about the transition from gconf to dconf.

---

### Post by bluexrider on 2012-01-15
> **vasa1 said:**
> bluexrider, you may also like to read [this]("http://askubuntu.com/questions/91403/when-to-use-gconf-vs-dconf"). It explains a bit about the transition from gconf to dconf.
Running 11.04 here, so as to your post, THANKS. I know DCONF is intended to replace the GCONF as has been used for years.

---

