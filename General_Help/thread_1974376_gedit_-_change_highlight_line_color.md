---
title: "gedit - change highlight line color"
date: 2012-05-06
forum: General Help
---

### Post by anejo on 2012-05-06
Currently even though in gedit prefs, 'highlight current line' is selected, the current line actually isn't.
The default color scheme is 'classic'.
If I select any other scheme, then I see a highlighted line but not so in classic.

Can one change the background color of the classic highlight color somewhere?
Thanks!

---

### Post by papibe on 2012-05-06
Hi anejo.

It does work here (10.04). May be it's a bug. What version of Ubuntu are you using?
Regards.

---

### Post by anejo on 2012-05-06
It's listed under the avatar...
And I recall it working okay in 11.10 too

---

### Post by anejo on 2012-05-31
OK, found a solution... finally!
I figured if the other Color Schemes could display a color there had to be a solution
I found these schemes are configured by xml files in /usr/share/gtksourceview-3.0/styles
It was easy enough to spot what was missing
For instance kate.xml has this line that classic.xml doesn't have
```
<style name="current-line"                background="#EEF6FF"/>
```
so, edit the classic.xml and simply add that missing line
and if you want, modify the color to your preference

---

