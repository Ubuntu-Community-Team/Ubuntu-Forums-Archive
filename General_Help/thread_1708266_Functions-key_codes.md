---
title: "Functions-key codes"
date: 2011-03-16
forum: General Help
---

### Post by ubu@ on 2011-03-16
Hi,

i'm trying to set the F-Keys [F1 - F12]. I have the Microsoft-wireless-laser (7000) keyboard, and of course its work fine in Windows, but in Ubuntu its not functioning. I tried all the scripts online but non of them helped. 

for example, 
```

#!/bin/sh
setkeycodes e00b 180
setkeycodes e011 181
setkeycodes e005 182
setkeycodes e015 183
setkeycodes e016 184
setkeycodes e073 185
setkeycodes e074 186
setkeycodes e075 187
setkeycodes e076 188
setkeycodes e077 189
setkeycodes e078 190
setkeycodes e03b 191
setkeycodes e008 192
setkeycodes e007 193
setkeycodes e03e 194
setkeycodes e03f 195
setkeycodes e040 196
setkeycodes e041 197
setkeycodes e042 198
setkeycodes e043 199 
setkeycodes e023 200
setkeycodes e057 201
setkeycodes e058 202
exit 0
```after running, I'm trying to "view lines number" in Kate editor (F11), and when pressing F11, I get an error:
[B][I]Error while trying to run (e057)
which is linked to the key (XF86Save)

[/I][/B]THANKS,
Ubu

---

### Post by vivek.pandey on 2011-03-16
try this
 
xmodmap -pke

you will get the codes for various keys and then write the script

---

### Post by ubu@ on 2011-03-16
I need to know which code to set to F11 (for example), I can't see how it direct me...

output cut:

~$ xmodmap -pke

```
...
keycode 200 = XF86TouchpadToggle NoSymbol XF86TouchpadToggle
keycode 201 =
keycode 202 =
...

```(I'm assuming 201 is F11...)

---

### Post by vivek.pandey on 2011-03-16
here i get my output


keycode  95 = F11 XF86_Switch_VT_11 F11 XF86_Switch_VT_11
keycode  96 = F12 XF86_Switch_VT_12 F12 XF86_Switch_VT_12
...

so check it out you will be having something similar

---

### Post by ubu@ on 2011-03-16
output cut for 93-97:

```
keycode  93 =
keycode  94 = less greater less greater bar brokenbar bar brokenbar
keycode  95 = F11 XF86_Switch_VT_11 F11 XF86_Switch_VT_11
keycode  96 = F12 XF86_Switch_VT_12 F12 XF86_Switch_VT_12
keycode  97 =
```


I still doesn't understand how can I set the F11 to function.

---

### Post by ubu@ on 2011-03-20
what do I missing?

---

### Post by mcduck on 2011-03-20
Have you tried using *xev* to check what keycodes the keys actally produce when pressed?

---

### Post by ubu@ on 2011-03-20
after using the command  *xev, *a white window pops and when pressing F11, the same error:
[B][I]
Error while trying to run (e057)
which is linked to the key (XF86Save)[/I][/B]

what does it mean?

---

### Post by mcduck on 2011-03-20
> **ubu@ said:**
> after using the command  *xev, *a white window pops and when pressing F11, the same error:
[B][I]
Error while trying to run (e057)
which is linked to the key (XF86Save)[/I][/B]

what does it mean?

Try removing the scripts (or whatever methods) you are now using to try to bind the key. They are what gives you the error report,a nd xev can't help with that. 

After that use xev again to check the keycode from the F11 key and edit your script accordingly.

---

### Post by ubu@ on 2011-03-24
.

---

