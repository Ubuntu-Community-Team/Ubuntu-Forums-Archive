---
title: "Backup files ending with ~"
date: 2012-01-18
forum: General Help
---

### Post by possumkeys on 2012-01-18
Hi All,
just a simple problem here. I go the terminal and list all the files in a folder where some of my files exist, e.g. Desktop.
For some files and even desktop shortcuts, there exists another copy that ends with ~. Now, I can't figure out what application is making these files but I'd love to disable it. Any help please?
UBUNTU 11.10
Thanks in advance!

---

### Post by sudodus on 2012-01-18
The tilde (~) backup file style comes from Unix. For example the editor ***emacs*** creates tilde backup files. I think you must figure out what software you are using and test if it creates such backup files.

Sometimes it is very valuable to have such backup files but to get rid of them you need to find what application creates them.

---

### Post by dcstar on 2012-01-18
> **sudodus said:**
> The tilde (~) backup file style comes from Unix. For example the editor ***emacs*** creates tilde backup files. I think you must figure out what software you are using and test if it creates such backup files.

Sometimes it is very valuable to have such backup files but to get rid of them if you find what application creates them.

Gedit, even OO used to IIRC. Mostly the issue comes under the heading "Big deal".

---

### Post by mcduck on 2012-01-18
...and keep in mind that pretty much every program that creates such backup files, also has the option to disable this feature if you want to.

For example in Gedit, go to Edit->Preferences, and on the Editor-tab uncheck the "Create a backup copy of files before saving"-option.

---

