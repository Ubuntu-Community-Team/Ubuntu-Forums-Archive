---
title: "help with modify this function"
date: 2009-10-07
forum: General Help
---

### Post by talphp on 2009-10-07
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
    gksudo "gnome-open $uri" &
    done

how can i modify it to open the file in GEDIT without sudo ??
Thanks

---

### Post by 3rdalbum on 2009-10-07
Remove the "gksudo" bit, remove the quotes, and change "gnome-open" to "gedit".

---

