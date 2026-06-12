---
title: "Made Compiz Menu Completely Transparent"
date: 2010-03-10
forum: General Help
---

### Post by Dragonlaw on 2010-03-10
I accidentally clicked on Compiz menu and set it to completely transparent. Now when I open the application I cannot readjust it back. Could anyone help me with this please?

---

### Post by eriktheblu on 2010-03-10
There are multiple compiz settings managers in the repos (or at least last I checked). Try installing another and see if you can correct it there.

I'm assuming that you only set your compiz settings application to invisible. Otherwise... wait for someone smarter than me.

edit to add:[This might work too](http://ubuntuforums.org/showthread.php?t=640199)

---

### Post by akand074 on 2010-03-10
Hold Alt + Scroll Up to make it less transparent.

Edit: Also now that I think about it you can also disable your proprietary drivers and compiz should deactivate then you can switch it back, then re-enable your drivers. Also going to your appearance menu and on the last tab (visual effects) I believe if you put "None" it may disable compiz. Anyway the first method should work by just Alt + Scroll

---

### Post by eriktheblu on 2010-03-10
^
|

See, much smarter than my ideas.

```
metacity --replace
```
To disable compiz
```
compiz --replace
```
To reinstate.

---

### Post by akand074 on 2010-03-10
> **eriktheblu said:**
> ^
|

See, much smarter than my ideas.

```
metacity --replace
```To disable compiz
```
compiz --replace
```To reinstate.

Oh man I've used that so many times I wonder why I didn't come up with that one! Yeah that is also a very good idea. I think by now your problem is solved because most if not all of these should work. Let us know if you managed to fix it or mark your thread as [solved]

---

### Post by Dragonlaw on 2010-03-10
Thanks! Alt-scroll up did the trick!

---

