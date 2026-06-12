---
title: "setting preferred applications eg VLC"
date: 2009-08-21
forum: General Help
---

### Post by charonred on 2009-08-21
A friend who is just starting out with Linux (Jaunty 9.04) wants to set VLC as the preferred app for DVDs; how does she set this as it's not listed as an option in 'Preferred Applications'

---

### Post by credobyte on 2009-08-21
Insert your DVD, click [COLOR=DarkGreen]Properties / Open With[/COLOR] and [COLOR=DarkGreen]Add[/COLOR].

---

### Post by charonred on 2009-08-21
thanks, thought it was something like that, I'll have to try it and any other suggestions when I go over there again; she's running 9.04, I'm running 8.04 and things are a little different.

---

### Post by ndtreviv on 2009-10-06
I have Jaunty and am trying to do the same thing.

I've inserted the disc, right clicked on the icon and chosen Properties - there's nothing in properties that lets me select the default application used to play the DVD.

So, I've tried Open With, and then chosen VLC, because it's on the list. VLC plays the DVD, but the next time a DVD is loaded, it runs movie player again. 

I've tried setting a Custom command in the Preferred Applications panel, that doesn't work either - it opens Movie Player whatever I select in there.

I'm totally new to Jaunty. What am I doing wrong?

---

### Post by charonred on 2009-10-06
I tested this in a Virtualbox install of Jaunty, so hopefully it works for you

go to System > Preferences > Preferred Applications

then go to the 'Multimedia' tab, then select the 'Custom' option and enter
```
vlc %f
``` and close,

then when I inserted a DVD, a dialogue window popped up asking what I prefer to open DVD with, I selected VLC and ticked 'always perform this action' :)

---

