---
title: "Screen Idle Time"
date: 2011-08-15
forum: General Help
---

### Post by xluryan on 2011-08-15
When I have the power option for "Dim Display When Idle" checked, how can I change the amount of time before Ubuntu thinks I'm idle?

I'm not talking about the screensaver, I'm talking about the option in the Power Management app.

Thanks :)

---

### Post by xluryan on 2011-08-18
Anyone?

---

### Post by tredegar on 2011-08-18
Maybe:
**gconf-editor** (install it if you do not have it).
Edit... Find... Idle
Under **/apps/gnome-power-manager/backlight/** change the value  for **idle_dim_time** from the default of **10**

---

### Post by xluryan on 2011-08-20
> **tredegar said:**
> Maybe:
**gconf-editor** (install it if you do not have it).
Edit... Find... Idle
Under **/apps/gnome-power-manager/backlight/** change the value  for **idle_dim_time** from the default of **10**

Perfect! That worked, thanks :)

---

