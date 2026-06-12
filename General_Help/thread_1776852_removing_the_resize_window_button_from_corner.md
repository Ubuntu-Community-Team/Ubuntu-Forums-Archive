---
title: "removing the resize window button from corner"
date: 2011-06-06
forum: General Help
---

### Post by floydian_slip on 2011-06-06
Hi,

I was wondering if it's possible to remove the triangular resize window button from the bottom-right corner of a particular window (or all windows, doesn't matter).

I recently made it so that I have a transparent terminal (with no title bar, borders, etc.) docked onto my desktop, but the one thing I can't get rid of is the ugly-looking resize button hanging out by itself in the middle of the screen.

Thanks!

---

### Post by Toz on 2011-06-06
Yes it is.
Create a file in your home directory called **.gtkrc-2.0** with the following contents:```
style "default-style"
{
  GtkWindow::resize-grip-height = 3
  GtkWindow::resize-grip-width = 3
}

class "GtkWidget" style "default-style"
```

Either log out and in again, or change the Appearance theme to something else and back.

A value of 3 hides the grips for me. You can go lower (all the way to 0) but I find a value of 0 makes it difficult for me to get the mouse in the right place to resize at all. A value of 3 is a good compromise for me.

---

### Post by floydian_slip on 2011-06-06
Thanks - worked like a charm.

I went down to 0 because I never use the resize grip anyway. My laptop screen is pretty small, so I generally keep all my windows maximized and simply toggle with Alt+F2. If I ever need to resize, I can just do the horizontal & vertical resizing separately - no big deal.

---

### Post by DobsonM on 2011-08-27
This doesnt seem to work in 11.10, anyone know how to remove the resize grips completely?

---

