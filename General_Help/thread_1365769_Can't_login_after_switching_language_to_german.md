---
title: "Can't login after switching language to german"
date: 2009-12-27
forum: General Help
---

### Post by chrisi99 on 2009-12-27
Hey there =)

I am currently trying to switch the system language to my mother-tongue .. german.

But after installing the language via administration->language support I just cant login anymore. The loginscreens jumps up and down for about 2 seconds... then I am at the login again.

When I switch back to english it works like a charm again...

what could cause this?

Using 9.10 and gnome btw =)

kind regards
chris

---

### Post by sisco311 on 2009-12-27
The German layout is QWERTZ. If you have a z/y or a non alphanumeric character in your password you have to type it according to the new keyboard layout (i.e. z instead of y).

---

### Post by chrisi99 on 2009-12-27
I thought of that, but thats not the case... switched the pwd to abc to make sure...

---

### Post by sisco311 on 2009-12-27
Well, the flickering means incorrect password.

Is the password recognized if you switch the keyboard layout to German?

```

setxkbmap de
pkexec echo "password test"
setxkbmap us
```

---

### Post by chrisi99 on 2009-12-27
> **sisco311 said:**
> Well, the flickering means incorrect password.

Is the password recognized if you switch the keyboard layout to German?

```

setxkbmap de
pkexec echo "password test"
setxkbmap us
```

yes, it works out ... 

dunno what i am doing wrong here...

---

### Post by chrisi99 on 2009-12-29
still not working... and ive no clue whats wrong =(

---

