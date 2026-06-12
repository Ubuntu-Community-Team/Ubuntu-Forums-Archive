---
title: "Possible to move CONKY to another screen?"
date: 2010-10-12
forum: General Help
---

### Post by I'm A Robot. Beep on 2010-10-12
Hi,
I use 2 monitors and Conky defaults to the top right of my right-hand monitor.
I'd like to move it to the top right of the left-hand monitor.

'alignment top_left' moves it to the left-hand monitor, but obviously the left-hand side. I need it on the right.

Is this possible?

Cheers for any help you can give
Dan

---

### Post by Pithikos on 2010-10-12
play around with this: ```
conky -x 300
```Where 300 is just the coordinates from the left to the right of the screen in pixels.
You can use the -y flag as well to set the coordinates on the y axis.

---

### Post by I'm A Robot. Beep on 2010-10-12
Found it...

```
gap_x 1450
```

 did the trick.
Cheers
Dan

---

### Post by johntaylor1887 on 2010-12-12
> **I'm A Robot. Beep said:**
> Found it...

```
gap_x 1450
```

 did the trick.
Cheers
Dan

Thanks for this, just what I was looking for. Except I had to make mine *gap_x 1279*.

---

