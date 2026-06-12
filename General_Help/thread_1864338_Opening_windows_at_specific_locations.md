---
title: "Opening windows at specific locations"
date: 2011-10-18
forum: General Help
---

### Post by Rikeshar on 2011-10-18
Is there a way to open windows in specific locations? I've got my TV set as a second display. In the nvidia settings the TV is to the right of my monitor, and my monitor is set as the main screen. However, most applications are opening up on the left side of the secondary display, and I cannot see them. Any help would be appreciated!

---

### Post by quadproc on 2011-10-18
> **Rikeshar said:**
> Is there a way to open windows in specific locations?

Perhaps.

If you are running X windows (you didn't say which graphics manager you are using) then some of the application programs recognize the _geometry_ argument.  You could try something like
```
someprogram -geometry 300x250+180-50
```Of course, substitute numbers corresponding to your preferences.

Sadly, many application programs do not honor the geometry argument.

You can learn much more about customizing the display from the web:
```
http://www.xfree86.org/current/X.7.html
```Check the [COLOR=Blue]geometry specifications[/COLOR] section.

quadproc

---

