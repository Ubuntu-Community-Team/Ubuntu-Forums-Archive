---
title: "problem loading indicator applets"
date: 2012-06-04
forum: General Help
---

### Post by rdh61 on 2012-06-04
Hi,

Just started using 12.04, and prefer to use the gnome desktop.

It was working fine the first few times, but at recent boots I've been getting the following error message:

"The panel encountered a problem while loading IndicatorAppletCompleteFactory: IndicatorAppletComplete".

All applets are then missing from my panel.

By googling I see others have had this issue from Ubuntu 11.10. It doesn't seem to have been solved and nobody seems to have a fix. As somebody pointed out, "this is a major usability issue".

Anybody here got any ideas?

Many thanks.

---

### Post by dino99 on 2012-06-04
from synaptic, remove all indicator-applet-*

---

### Post by rdh61 on 2012-06-05
Thanks. How would that solve the problem of not having the applets? Drag and drop what I want to the panel? I notice this version of the panel does not have the right click "add to panel" feature.

Thankfully the issue seems to have righted itself so I'll take no action and wait and see.

_If it recurs_ I'll try the following:

1) I recall the behaviour started after I dragged and dropped an applet onto the panel (gnome-ppp). I'll remove that to see if the issue is immediately solved.

2) However, it is useful to be able to add things to the panel. So I'll then add it back and try the following. Remove indicator-applet-complete with synaptic and instead install indicator-applet and indicator-applet-session. I notice the first was not installed on an older, trouble free release (10.04), while the latter two were. The converse is the case with 12.04.

I'll keep you posted.

---

