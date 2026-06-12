---
title: "Copy/Move to Other Pane with Sudo in Nautilus"
date: 2010-10-13
forum: General Help
---

### Post by timur_ba on 2010-10-13
There are right-click commands "Copy/Move to Other Pane" in Nautilus. It's very nice. But, what do we do when we have "permission denied"? I just hate when I have that message and no option to enter password.
Can we create "Copy/Move to Other Pane with Sudo"? Or just "Copy with Sudo" and then Paste? I couldn't find the original scrips to try to change them. If %M is a usual parameter, what is the parameter for other pane? 
I would really like to keep dual pane on all the time, but don't know how to do it.

---

### Post by VMC on 2010-10-13
> **timur_ba said:**
> There are right-click commands "Copy/Move to Other Pane" in Nautilus. It's very nice. But, what do we do when we have "permission denied"? I just hate when I have that message and no option to enter password.
Can we create "Copy/Move to Other Pane with Sudo"? Or just "Copy with Sudo" and then Paste? I couldn't find the original scrips to try to change them. If %M is a usual parameter, what is the parameter for other pane? 
I would really like to keep dual pane on all the time, but don't know how to do it.

Most likely its own by root. If you know what your moving then do this:
Alt+F2, then enter ```
gksu nautilus
```. then give you password. Now you can move anything, it starts in "roots" directory, but careful of what your moving, if it involves anything outside your home directory

---

