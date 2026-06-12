---
title: "where are my network folders... :-S"
date: 2010-07-20
forum: General Help
---

### Post by cje on 2010-07-20
A really, really stupid question; where are my network folders? :-S

In "explorer" my network folders are listed on the low left side. But, when I'm trying to attach a file in an email from a shared network folder the list of networks has disappeared? Where may I find those shares now?

Running Ubuntu Netbook Remix 10.04

---

### Post by darolu on 2010-07-20
If your network is set (i.e. samba is installed and configured) they are under "Network"; click on Places (top-left menu) and then on Network, all shared resources should be listed there.

You can also press Ctrl+L in Nautilus to type the entire route to your shared directory.

---

### Post by Morbius1 on 2010-07-20
When you connect to a shared folder from "Network" in Ubuntu it creates a mountpoint at:
> /home/your_user_name/.gvfsThe problem is the ".gvfs". The "." before the gvfs indicates that it is a "hidden" folder. To see the "hidden" folder in Nautilus you need to make a change:
Nautilus > Edit > Preferences > Views > "Show hidden and backup files"

To see it in your email client you need to right click on an open space in the "Attach Files" box and select: "Show hidden files"

The developers would have made life a lot simpler had they not made it hidden.

---

### Post by cje on 2010-07-20
Ahh! Hidden files! That's it!  Thanks a lot!

:-)

---

