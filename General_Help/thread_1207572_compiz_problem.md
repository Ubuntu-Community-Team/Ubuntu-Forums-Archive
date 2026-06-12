---
title: "compiz problem"
date: 2009-07-08
forum: General Help
---

### Post by shaullx on 2009-07-08
First of all i just wanna say that i've searched all over google and here for a solution and none worked for me

Compiz fusion is autostarting, i added fusion icon aswell to autostart
but still to enable compiz effects I need to right click 'fusion-icon' and select "Reload window manager"
otherwise it just won't work..
i tried to add to the autostart 'compiz --reload', 'fusion-icon --no-start'
and in the configuration manager the default 'window manager' is set to compiz
but still i need to reload window manager so the effect will enable
its driving me crazy :(
any help will be appreciated

---

### Post by chriskin on 2009-07-08
a good idea would be to add this line to the startup applications 

```
compiz --replace
```


it will most probably work

---

### Post by shaullx on 2009-07-08
> **chriskin said:**
> a good idea would be to add this line to the startup applications 

```
compiz --replace
```


it will most probably work

It was one of the first things i did (i misspelled replace with reload in the post im sorry i will fix it now)

---

### Post by chriskin on 2009-07-08
if it still doesn't work though, tell me (/us) and i (/we) will try again :P

---

### Post by shaullx on 2009-07-08
> **chriskin said:**
> if it still doesn't work though, tell me (/us) and i (/we) will try again :P

i just tried and no i still need to reload manually

---

### Post by chriskin on 2009-07-08
most probably you didn't remove the other compiz workarounds you have at the startup apps?

or you didn't write two "-" at compiz --replace?

---

### Post by shaullx on 2009-07-08
> **chriskin said:**
> most probably you didn't remove the other compiz workarounds you have at the startup apps?

or you didn't write two "-" at compiz --replace?

nope only 'compiz --replace' is there and i used two '-'

---

### Post by shaullx on 2009-07-08
BTW if i run in terminal compiz --replace all window borders are gone.
and if i run it again then they come back and compiz effects are enabled

---

### Post by chriskin on 2009-07-08
oh, this happened to me before as well

i was missing some packages compiz needs, try searching at synaptic for compiz and add those that are about decoration

and make sure that at compiz's plugin decoration, the command is gtk-window-decorator --replace


mine had both wrong - yet that might have been my installation's problem and not yours...i don't know :S

---

### Post by shaullx on 2009-07-08
> **chriskin said:**
> oh, this happened to me before as well

i was missing some packages compiz needs, try searching at synaptic for compiz and add those that are about decoration

and make sure that at compiz's plugin decoration, the command is gtk-window-decorator --replace


mine had both wrong - yet that might have been my installation's problem and not yours...i don't know :S

Solved!
i tried installing few packages related to compiz logged out and logged back in and it works:)
Thank you!:)

---

