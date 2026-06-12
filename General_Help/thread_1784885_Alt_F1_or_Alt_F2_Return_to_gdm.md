---
title: "Alt F1 or Alt F2 Return to gdm"
date: 2011-06-17
forum: General Help
---

### Post by Robbyx on 2011-06-17
Short of a reboot how do I return to the gdm if I have had to press Alt F2 because the screen has frozen.

'service gdm start' at the terminal  gives the following  error messages and fails to reload the GDM:

[I]Start: reject message, 1 matched rules;
type 'method call', sender '1.79'(uid=1000 pid =4163 com = '-naln chw'
interface ='com.ubuntu.upstart0-6.job'
member ='start'
error name = '(unset)'
requestd_supply = 0
destination = 'com.ubuntu.upstart'
[/I]

Is there a way of getting back into the gdm?

---

### Post by Frogs Hair on 2011-06-17
If you used Ctrl Alt F1 , Ctrl Alt F7 will bring you back .

---

### Post by Robbyx on 2011-06-17
Thank you. That worked well. I await a screen freeze with renewed hope.

---

