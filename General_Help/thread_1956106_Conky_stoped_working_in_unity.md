---
title: "Conky stoped working in unity"
date: 2012-04-10
forum: General Help
---

### Post by daftlad on 2012-04-10
My conky does not show up in Unity, 11.10 anymore, works fine in GNOME classic and GNOME classic(no effects), but does not work in Unity or Gnome. If I start it from the terminal it says its running and gives no faults, just not showing up on desktop.

---

### Post by alex2e1gzy on 2012-04-12
Have you tried setting   [FONT=&quot]own_window_type override
[/FONT]
  to
 [FONT=&quot]own_window_type desktop
[/FONT]
  
Also, if you run Conky from a terminal, what output do you get?

---

### Post by daftlad on 2012-04-12
> **alex2e1gzy said:**
> Have you tried setting   [FONT=&quot]own_window_type override
[/FONT]
  to
 [FONT=&quot]own_window_type desktop
[/FONT]
  
Also, if you run Conky from a terminal, what output do you get?


Yes I tried that, but its been working fine for a long time, just wont work in unity or gnome shell anymore. 
I get no error message from the terminal, just this

Conky: desktop window (1c00095) is subwindow of root window (1ad)
Conky: window type - override
Conky: drawing to created window (0x2400001)
Conky: drawing to double buffer

I am going to fit a new HD on the weekend and will and will restore a fresh install of 11.10. So that should take care of it. 
Thanks

---

### Post by alex2e1gzy on 2012-04-13
With your Conky file, I also get the same behavior, nothing shows up!

When I disabled the lua entries (because I don't have your script) and changed the window type to normal (or desktop) I can then see your Conky running. Double check

own_window_type normal

BTW - I love the font you are using!

---

### Post by daftlad on 2012-04-13
That did the trick, thanks a lot and yes that font is pretty cool.

---

