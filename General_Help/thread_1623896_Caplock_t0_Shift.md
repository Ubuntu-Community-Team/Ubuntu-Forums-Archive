---
title: "Caplock t0 Shift"
date: 2010-11-17
forum: General Help
---

### Post by Bob Fletcher on 2010-11-17
I know there is a lot posted about the Capslock but noting is very clear to me anyway. It seems most people want to turn it in to a CTRL key.
I have tried to remap it = System>Preferences>Keyboard>keyboard preferences>layout>Options. The only option that seems to work is to disable it altogether. All the other Shift options has it just working like a normal shift key.
So can some tell me what file to edit and what to change in it so my Capslock becomes a Shift.
Thanks
Robert...
Ubuntu 10:10

---

### Post by Bob Fletcher on 2010-11-17
I have not had reply in the last 10 hours but in that time I have been reading up on what I am supposed to do.
xmodmap seems to be the thing but I have a problem. I can stop it working but it I played around with it at the command level but it never changes. I tried this
```
xmodmap -e 'keycode 42 = Shift_L'
```
was accepted without error but no changes.
I am still very confused on this. Remapping in Windows was very easy.
Robert

---

### Post by gmargo on 2010-11-17
To turn the CapsLock key into an additional Shift-left key, put the following text into a file and run "xmodmap" on that file (tested on USA keyboard):

```

keycode 66 = Shift_L
clear Lock
add Shift = Shift_L

```

---

### Post by Bob Fletcher on 2010-11-17
> **gmargo said:**
> To turn the CapsLock key into an additional Shift-left key, put the following text into a file and run "xmodmap" on that file (tested on USA keyboard):

```

keycode 66 = Shift_L
clear Lock
add Shift = Shift_L

```

Thank you so much I was almost giving up. Now how do I make those changes permanent. I tried putting it in a file called .xmodmap in my home directory but that did not work.

---

### Post by Bob Fletcher on 2010-11-17
I worked it out the file was .Xmodmap it is working now. In Australia we use US Keyboard but in the UK now and the CapLock key is a huge thing and a tine Shift key. I am very happy now.

---

### Post by Bob Fletcher on 2011-01-23
> **gmargo said:**
> To turn the CapsLock key into an additional Shift-left key, put the following text into a file and run "xmodmap" on that file (tested on USA keyboard):

```

keycode 66 = Shift_L
clear Lock
add Shift = Shift_L

```

I know this is a while and I gave up on that installation. I am sure it worked then.
The question is how do I get xmodmap to execute the file on startup? I find I have to run it manually at startup.

---

### Post by Bob Fletcher on 2011-01-23
Did this all by myself in the startup programs. Sorry if I waited time.
Robert...

---

