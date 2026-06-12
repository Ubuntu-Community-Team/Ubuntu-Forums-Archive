---
title: "Create new tool for Gedit LaTeX Plugin"
date: 2011-01-17
forum: General Help
---

### Post by looreenzoo on 2011-01-17
Hi all,
I would like to create a new tool for the Gedit LaTeX Plugin, but I run into two problems. First, I cannot select "New" from *Edit / Preferences / Plugins / LaTeX Plugin 0.2 / Configure Plugin / Tools. *I tried first the version in the ubuntu repositories and then the version on Sourceforge, but both don't allow to create a new tool: the button is there, but if I click on it, nothing happens. Second, if I edit one of the existing tools, I really don't have an idea on how to change the relevant commands. I tried with:
```
latex
bibtex
latex
pdflatex
evince
```but it obviously doesn't work.
Can you advise me on that? Thank you in advance!

---

### Post by mista_freeze on 2011-10-07
had the same problem after a fresh ubuntu 11.04 installation. the bug and a solution is reported here:
[http://sourceforge.net/tracker/index.php?func=detail&aid=2991059&group_id=204144&atid=988428](http://sourceforge.net/tracker/index.php?func=detail&aid=2991059&group_id=204144&atid=988428)

you need to restart gedit after editing the dialog.py file

edit:
the file dialog.py is in the folder
/usr/lib/gedit-2/plugins/GeditLaTeXPlugin/src/preferences/

---

### Post by looreenzoo on 2011-10-08
> **mista_freeze said:**
> had the same problem after a fresh ubuntu 11.04 installation. the bug and a solution is reported here:
[http://sourceforge.net/tracker/index.php?func=detail&aid=2991059&group_id=204144&atid=988428](http://sourceforge.net/tracker/index.php?func=detail&aid=2991059&group_id=204144&atid=988428)

you need to restart gedit after editing the dialog.py file

edit:
the file dialog.py is in the folder
/usr/lib/gedit-2/plugins/GeditLaTeXPlugin/src/preferences/

Thank you! Although in my case dialog.py is in the folder:
~/.gnome2/gedit/plugins/GeditLaTeXPlugin/src/preferences

---

