---
title: "Weird touchpad problem"
date: 2011-02-16
forum: General Help
---

### Post by baillou2 on 2011-02-16
So I was having the issue with the touchpad on my hp Pavilion freezing up the gnome desktop when it was enabled (click the little button from orange to blue). I never cared much about this since I always use my mouse. But recently I figured out how to:

 "xinput set-prop 13 "Device Enabled" 0/1"

This actually solved both the freezing problem AND made the touchpad work too once I re-enabled it.

But now I can't seem to re-enable it. I try toggling the variable from 0 to 1 by typing "xinput set-prop 13 "Device Enabled" 1, but nothing happens. It still shows as "0".
I even went to the preferences under System and made sure the "enable touchpad" was checked, and indeed it is, but no go.

What could be causing this?

Thanks in advance.

David.

---

