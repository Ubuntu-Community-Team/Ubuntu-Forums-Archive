---
title: "Gedit window is not visible"
date: 2012-02-10
forum: General Help
---

### Post by flatko on 2012-02-10
Hi all.
Recently I installed Oneiric on my PC (it was running Lucid before) and I can't open Gedit as a regular user. In System monitor it shows the gedit process, but there's no window anywhere. Opening in terminal doesn't show errors, but still no window. If I run Gedit as root, it's working.
If it's important, GPU is GeForce 5200 with the proprietary Nvidia driver.

---

### Post by hwttdz on 2012-02-10
If you haven't can you quit gedit and try again?  

Which window manager are you using?  

Can you alt+tab to it?

What if you try "gedit --new-window"?

What about "wmctrl -R gedit"? (you may need to install wmctrl, also I'm not sure if wmctrl plays well with all window managers). 

I'm kind of shooting in the dark, but my first guess would be it's more window manager related than gedit related.

---

### Post by flatko on 2012-02-10
> **hwttdz said:**
> If you haven't can you quit gedit and try again?  

Which window manager are you using?  

Can you alt+tab to it?

What if you try "gedit --new-window"?

What about "wmctrl -R gedit"? (you may need to install wmctrl, also I'm not sure if wmctrl plays well with all window managers). 

I'm kind of shooting in the dark, but my first guess would be it's more window manager related than gedit related.

Hi and 10x for the reply!
I'm using Unity. Just tried it in Gnome classic and it opens with no problem, so you're right - it's a Unity bug.
In Unity alt+tab doesn't show the Gedit window. The option  --new-window has no result (just like with no option).
I installed wmctrl and tried to focus the Gedit window - it only removes focus from the terminal ](*,)](*,)

---

