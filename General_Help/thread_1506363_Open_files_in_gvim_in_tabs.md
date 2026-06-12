---
title: "Open files in gvim in tabs?"
date: 2010-06-10
forum: General Help
---

### Post by trancer_ on 2010-06-10
Hello.

Is it possible to open text files in gvim in tabs not opening anothe rgvim window for every text file? Just like it is done in gedit: open a file the open another file and it opens in a tab.

Thanks.

---

### Post by gmargo on 2010-06-10
To get **gvim** to open a file in a new tab of a pre-existing window, and not open a new window (unless one does not exist), use the "--remote-tab-silent" option.

You can make this work from Nautilus by creating a new text file association with the command "gvim --remote-tab-silent".  You could also do it by editing the appropriate gvim.desktop file(s).

---

### Post by trancer_ on 2010-06-13
> **gmargo said:**
> To get **gvim** to open a file in a new tab of a pre-existing window, and not open a new window (unless one does not exist), use the "--remote-tab-silent" option.

You can make this work from Nautilus by creating a new text file association with the command "gvim --remote-tab-silent".  You could also do it by editing the appropriate gvim.desktop file(s).

Thanks! That worked for me.

---

