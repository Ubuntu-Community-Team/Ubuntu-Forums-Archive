---
title: "gvim window size matches terminal window size"
date: 2011-05-31
forum: General Help
---

### Post by Pug226 on 2011-05-31
Gvim matches the terminal (gnome-terminal or xterm) window size upon startup. Exporting LINES or COLUMNS doesn't change the gvim window size, but resizing the terminal changes the geometry when gvim starts. Setting COLUMNS and LINES in gvim's startup files override this behavior. Where does gvim get the window geometry information?

To see this in action, open an xterm or gnome-terminal. Resize it to be very wide or very tall. Run gvim and the gvim window will match the terminal window. Close gvim and resize the terminal. Opening gvim again will show gvim matches the new terminal size.

This happens for both vim.gnome (2:7.2.330-1ubuntu4) and vim.gtk (2:7.2.330-1ubuntu4) (soft linked to gvim) on Ubuntu 10.10. I have also tested this with vim-gnome (2:7.3.035+hg~8fdc12103333-1ubuntu7) on Ubuntu 11.4.

Does anyone else see this behavior? Was it always like this?

---

### Post by Raleke on 2012-09-05
I'm not sure what triggers this behavior, but I've found a way around it.

In your .gvimrc you can configure the starting size of gvim.  This is mine:

set lines=60 columns=230

---

