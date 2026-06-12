---
title: "restoring mouse defaults"
date: 2010-06-12
forum: General Help
---

### Post by bobdobbs on 2010-06-12
Hi all.

I was messing around with games on my desktop.
I'm using lynx, relatively newly installed.

I changed the mouse controls in one of the games to be more sensative for movement.

I've got problems now. :(

It seems like whenever I click on a windowframe in gnome, half the time the windowframe treats my click as a doubleclick.
The results are really frustrating.

For days I've been messing around with the mouse settings under system>preferences, but I can't seem to get the settings right.

Knowing linux, the mouse controls have to be set in a text file somewhere.

Can anyone help me to reset my mouse preferences to the original defaults ?

Thanks.

---

### Post by golanbatrac on 2010-06-12
1. Press **Alt + F2**
2. type **gconf-editor** -- Press **enter**
3. In the left sidebar click **desktop > gnome > peripherals > mouse**
4. default settings: double_click = 400; drag_threshold = 8; motion_acceleration = -1; motion _threshold = -1; single_click is checked

---

### Post by bobdobbs on 2010-06-13
> **golanbatrac said:**
> 1. Press **Alt + F2**
2. type **gconf-editor** -- Press **enter**
3. In the left sidebar click **desktop > gnome > peripherals > mouse**
4. default settings: double_click = 400; drag_threshold = 8; motion_acceleration = -1; motion _threshold = -1; single_click is checked

Thanks.

I've reset to those settings.

Unfortunately, the problem persists.

I rebooted, and the problem still persists.

This sucks. It's getting really frustrating. I've got work that I have to do, but it's really distracting having window frames randomly close when I select them.

---

### Post by bobdobbs on 2010-06-21
Bump

My mouse is still acting all crazy.

It's driving me nuts.

How do I make it behave ?

---

### Post by golanbatrac on 2010-06-21
Have you tried a different mouse?

---

### Post by bobdobbs on 2010-06-21
> **golanbatrac said:**
> Have you tried a different mouse?

Yes. Same results.

I've also tested the current mouse on a different machine.

The mouses seem to be fine.

---

