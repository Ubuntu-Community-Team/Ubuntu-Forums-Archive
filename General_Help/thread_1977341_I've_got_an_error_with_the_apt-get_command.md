---
title: "I've got an error with the apt-get command"
date: 2012-05-10
forum: General Help
---

### Post by enterdavertex on 2012-05-10
When i'm tryng this command to update my system , it says : W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
 

i tried to delete the files specified but no work.

---

### Post by plucky on 2012-05-10
> **enterdavertex said:**
> When i'm tryng this command to update my system , it says : W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
 

i tried to delete the files specified but no work.

You need to look in your **Software Sources** and remove one of the dl.google.com entries and then delete the list files that have already been created,before the error will go away.

OR

Post the output for these commands in a terminal ```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list
``` so we can see what your sources look like.

Good Luck

---

