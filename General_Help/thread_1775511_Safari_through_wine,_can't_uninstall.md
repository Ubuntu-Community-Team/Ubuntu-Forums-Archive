---
title: "Safari through wine, can't uninstall"
date: 2011-06-04
forum: General Help
---

### Post by griffsterb on 2011-06-04
So I used Wine to install Safari. First time I run Safari, it crashes. So I 'uninstall' it with Wine, except predictably Safari still opens after the uninstall. How would I go about removing Safari completely from Ubuntu? I can't even find my wine directory.

---

### Post by WorMzy on 2011-06-04
Press Ctrl+H in nautilus to see "hidden" folders. .wine (and, indeed, *all* folders beginning with "." are hidden). No idea where Safari would be installed to, aside from the fact that it'd be under .wine.

Probably under .wine/Program\ Files/Safari, or some similar path. Delete the folder and the program will be as good as "uninstalled".

---

