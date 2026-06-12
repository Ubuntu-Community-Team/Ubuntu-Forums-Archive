---
title: "Please Help Me Find an Icon for GVim"
date: 2009-10-05
forum: General Help
---

### Post by navneeth on 2009-10-05
*Stupid action ahead*

For some silly reason, I deleted GVim's entry from the Main Menu (Applications->Accessories). [I wanted to shift it to the Programming menu, but why I deleted the existing one while I could've simply unchecked it, no one knows.]

Now, I can create an entry for GVim, but I'm not able to find an icon to put next to the entry. There are no SVG icons available in [Vim's website](http://www.vim.org/logos.php). Where can I get an icon that would work?

---

### Post by squaregoldfish on 2009-10-05
You could try reinstalling the gvim package through synaptic - this should reinstall all the files, including the icon.

Steve.

---

### Post by navneeth on 2009-10-05
Hi, squaregoldfish. I tried that. Purged all the files that were installed, in fact. Didn't work. 

Exact command, if you're interested. 

```
sudo apt-get purge vim-gui-common vim-gnome tcl8.4 libruby1.8 vim-runtime 

```

---

### Post by navneeth on 2009-10-05
Oh, found it. /usr/share/pixmaps/vim.svg.

---

