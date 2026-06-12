---
title: "Deleting unwanted themes, no longer working"
date: 2011-09-10
forum: General Help
---

### Post by Tornikee on 2011-09-10
Hello, I had been using the Alt-F2 > ```
gksu gnome-appearance-properties
``` method for deleting unwanted themes on 11.04, although some time ago this ceased working - after running the mentioned command and entering the admin password, the 5-7 second loading comes to nothing – the ‘delete’ button is still grayed out. What can be the reason for this?

Thanks in advance.

---

### Post by llamabr on 2011-09-10
Why do you need sudo for this?  Try opening a terminal and type:

```
gnome-appearance-properties
```

and report any errors

---

### Post by Tornikee on 2011-09-10
> **llamabr said:**
> Why do you need sudo for this?  Try opening a terminal and type:

```
gnome-appearance-properties
```

and report any errors

Thanks for the reply. Typed that, went to the themes, and there are some entries in 'controls' and 'window border' I can delete, but the delete button is still grayed out for some. There is the continuous "/home/tornike/.gtkrc-2.0:1: error: unexpected character `\342', expected string constant" error in the terminal window.

---

### Post by Tornikee on 2011-09-11
Any other methods of solving this?

---

