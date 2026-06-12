---
title: "How to remove the new thin dark line in 10.10 Windows?"
date: 2010-10-12
forum: General Help
---

### Post by mixim on 2010-10-12
Hello guys, liking the enhanced look of 10.10 so far... except one thing...

Look in the attached picture (I've enhanced it to see the line more clearly), or at your own window if you are running 10.10... 

Between the title bar and the application bar there is now a very very thin indented line separating the two.

1. Why is it even there? Makes it look worse than in 10.04 !

2. How do I get rid of it, but still keeping the new default theme?

Regards// Joakim from Sweden

---

### Post by DTHCND on 2010-10-12
I'm curios too... I just noticed that, but it looks like it's only on some programs (I don't see it on chrome/update manager)... I guess the don't have File, Edit, View, etc though...

---

### Post by mixim on 2010-10-15
> **DTHCND said:**
> I'm curios too... I just noticed that, but it looks like it's only on some programs (I don't see it on chrome/update manager)... I guess the don't have File, Edit, View, etc though...

Yeah exactly, it doesn't show when there is no menun- or context bar in the window... Well, either way it looked "much more" cohesive before...

---

### Post by luvshines on 2010-10-15
Which theme is it ?

---

### Post by mixim on 2010-10-15
> **luvshines said:**
> Which theme is it ?

It's bone stock 10.10 default... Radiance and Ambiance... Although in that pic i've cranked up the contrast and brightness to distinguish the line (Might not normally be seen on darker displays).

Also I said before, is not present in 10.04.

---

### Post by NoVista on 2010-10-15
I have a dark theme here, it is visible.
The white you see between the two was not there before.

---

### Post by mixim on 2010-10-16
> **NoVista said:**
> I have a dark theme here, it is visible.
The white you see between the two was not there before.

Ahh, so it seems Gnome-related rather than Theme-related then? Any others with other themes and this problem?

---

### Post by luvshines on 2010-10-16
> **mixim said:**
> Ahh, so it seems Gnome-related rather than Theme-related then? Any others with other themes and this problem?

It is not there in New Wave, right ??

AFAIK, it is all controlled from this file:
```

/usr/share/themes/<theme-name>/metacity-1/metacity-theme-1.xml

```

If you open that file for New Wave, you'll see that following lines are commented:
```

<!-- line color="shade/#696969/1.0" x1="0" y1="top_height-2" x2="width" y2="top_height-2"/>
<line color="shade/#696969/1.0" x1="0" y1="top_height-1" x2="width-1" y2="top_height-1"/ -->

```

If you uncomment them even New Wave gets screwed

I tried to tweak Ambiance's control file, but with no success :(

---

