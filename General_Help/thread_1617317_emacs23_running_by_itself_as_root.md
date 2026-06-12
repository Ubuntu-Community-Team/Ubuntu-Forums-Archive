---
title: "emacs23 running by itself as root?"
date: 2010-11-09
forum: General Help
---

### Post by cthulhu_54 on 2010-11-09
I'm using emacs23, and almost every time I start my computer, within 10 minutes the hard drive starts to spin at maximum, and the CPU goes up to 100%. Running htop, I see that it is emacs23 being run by root, with the command flag:
emacs23 --funcall TeX-auto-generate-global

Now what the duce is this? I use AUCTeX regularly, but I don't have anything like this in my .emacs-file, and I've tried google, but I can't find anything about how to turn this off! 

It seems like this is a command one is recommended to run after an installation, but I don't want my computer to run this nonsense command. Anybody know how I can deactivate this?

---

