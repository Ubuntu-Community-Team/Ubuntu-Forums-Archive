---
title: "Remapping capslock - wasn't solved yet!"
date: 2010-01-02
forum: General Help
---

### Post by VitaminCPP on 2010-01-02
I don't want the capslock key to be disabled completely. I want it to change layout, and only it. Without lightening this LED on the keyboard and doing usual capslock task. I am already saying that the usual 
```
xmodmap -e "remove lock = Caps_Lock" 
``` 
didn't do it for me. All things I've tried either disable capslock completely or turning it on with 2 features: rolling layout AND enabling/disabling this LED on the keyboard. I want just to switch layout.

And I've googled. Really.

Thanks.

---

### Post by VitaminCPP on 2010-01-03
bump

---

### Post by VitaminCPP on 2010-01-03
anyone?

---

### Post by ibuclaw on 2010-01-03
What do you intend to remap it to?

---

### Post by VitaminCPP on 2010-01-03
changing layout. Let's say, left alt+left shift

---

### Post by VitaminCPP on 2010-01-04
bump...

---

### Post by VitaminCPP on 2010-01-04
I found the way to do what I wanted:

1. Create ~/.Xmodmap (~ is your home directory)

2. Write the following in Xmodmap:
```
clear Lock
keycode 66 = ISO_Next_Group

```

3. Logout

That's it!

---

