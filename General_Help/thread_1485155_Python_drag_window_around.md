---
title: "Python drag window around"
date: 2010-05-16
forum: General Help
---

### Post by AshRice on 2010-05-16
I'm trying to manipulate the existing windows from within a python script similar to the BASH wmctrl. I've got the basics down with PyWnck, but I need to be able to tell when a window is actively being dragged (or just when the title bar is being clicked). I doubt this is a wnck function.

Can somebody please point me in the direction of the right python package?

---

### Post by AshRice on 2010-05-18
Found a workaround for what I need, but I ran into a new problem. I cant seem to be able to update the location of the current window while it is being moved around, so I have to move it into position and then reactivate the edge binding (Compiz) to get the script to execute. I've tried .force_update() to no avail.

Thoughts?

---

