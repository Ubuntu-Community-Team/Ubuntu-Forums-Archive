---
title: "(nero:12026): Gtk-CRITICAL **: gtk_tree_view_scroll_to_cell: assertion `tree_view-&gt;pr"
date: 2009-09-11
forum: General Help
---

### Post by sprilutsky on 2009-09-11
After I applied the ubuntu (ubuntu 9.0.4) recommended updates, Nero 3.5.3.1 for linux 64 bit hangs with message:
(nero:12292): Gtk-CRITICAL **: gtk_tree_view_scroll_to_cell: assertion `tree_view->priv->tree != NULL' failed
 tsp0001@desktop1:/media/Second Disk/Downloads$ nero &
[1] 12026
tsp0001@desktop1:/media/Second Disk/Downloads$
(nero:12026): Gtk-CRITICAL **: gtk_tree_view_scroll_to_cell: assertion `tree_view->priv->tree != NULL' failed
 tsp0001@desktop1:/media/Second Disk/Downloads$ ps -ef |grep nero
tsp0001  12026  3679  7 17:23 pts/0    00:00:21 nero
tsp0001  12044  3679  0 17:28 pts/0    00:00:00 grep nero

---

