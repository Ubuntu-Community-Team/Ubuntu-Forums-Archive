---
title: "Bash command to check if a window is active?"
date: 2009-12-01
forum: General Help
---

### Post by Koalano on 2009-12-01
Hi friends,

Is there a bash command to check if a specific window is active? For example, I want to check if Firefox (or ThunderBird, or StarDict etc.) is currently active, which command can I use to do that?

Thanks for reading my question.

regards,

Koalano.

---

### Post by MelDJ on 2009-12-01
top

---

### Post by Koalano on 2009-12-02
> **MelDJ said:**
> top

I'm sorry because I did not explain my question clearly enough. 

By 'active' I mean the window which currently gains focus, or the window with which the user is currently working/interacting (Therefore I used the word 'window' instead of 'program' or 'process').

---

### Post by DaithiF on 2009-12-02
you can get the title of the currently focused window with a combination of the xprop and xwininfo tools like this:
```
xwininfo -id $(xprop -root | awk '/NET_ACTIVE_WINDOW/ { print $5; exit }') | awk -F\" '/xwininfo:/ { print $2; exit }'

```

the xprop command gets the id of the active window, the xwininfo command then dumps out information about that window, one of whose lines contains the window title.

---

### Post by Koalano on 2009-12-04
Hi DaithiF,

Thank you very much for your answer. That's exactly the thing I need.

---

### Post by DaithiF on 2009-12-04
my pleasure, happy to help.

---

### Post by kaibob on 2009-12-04
DaithiF

Thanks for the post. I have been looking for a way to do this.

The other day, a forum member posted some information concerning the xdotool utility, which I have found to be very useful. I was curious if it would work with your command. It does and this is an alternative (but certainly no better) way of getting the title of the active window.

```
xwininfo -int -id $(xdotool getactivewindow) | awk -F\" '/xwininfo:/ { print $2; exit }'
```

Thanks again.

kaibob

---

