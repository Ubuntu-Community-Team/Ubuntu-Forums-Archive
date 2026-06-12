---
title: "Setting defaults"
date: 2011-11-22
forum: General Help
---

### Post by atothec on 2011-11-22
Hi,

I changed the side which the close/maximize/minimize buttons appear on a window a few months ago and would like to set it back to the default. Is there any way to set things back to their default setting?

---

### Post by ajgreeny on 2011-11-22
Which version of ubuntu?  Normally the easiest way to do it is with gconf-editor-> apps ->metacity ->general ->button_layout.  I think that will also work in 11.10.

The value should be a string, such as "menu:minimize,maximize,spacer,close"; the colon separates the left corner of the window from the right corner, and the button names are comma-separated.  To change button sides you therefore need to put the colon in the correct position for your needs.

---

