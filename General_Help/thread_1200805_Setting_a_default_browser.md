---
title: "Setting a default browser?"
date: 2009-06-30
forum: General Help
---

### Post by AoSteve on 2009-06-30
I've been searching for something a little less.. resource mongering then firefox and found that epiphany fits the bill and it was in the repo's.   However, whenever I select something that opens a browser, such as my RSS feed list that automatically opens my browser to the post I select, firefox starts.   I would rather keep firefox installed as a backup but don't want it to be the default browser.

So my question is, how do I set epiphany as the default browser for all of the applications that open a browser or new tab in a browser?

Thanks ahead of time,
Steve

---

### Post by Elfy on 2009-06-30
System > Preferences > Preferred Applications - internet tab

---

### Post by Bucky Ball on 2009-06-30
System->Preferences->Preferred Applications

---

### Post by fooman on 2009-06-30
in jaunty,  go to system > preferences > preferred applications.

on the internet tab > web browser....see if epiphany is on the list,  if not choose "custom" and enter "epiphany %s"  as the command.

hope that helps.

edit....i am soooo slow.  someone always beats me to the punch!

---

### Post by darthmob on 2009-06-30
DUNDUNDUN it just happens that I had the same problem yesterday. Simply start up a terminal of your likings and use the command
```
update-alternatives --config x-www-browser
```.
if it complains about missing rights you have to put a sudo in front of it.

---

### Post by AoSteve on 2009-06-30
Thank you everyone...   LOL!   I didn't realize preferred applications was ever there!   I never do much opening of applications by clicking files.  I almost always have an url shot at me through the IM and I really am starting to like epiphany more then FF.   :)

Thank you everyone!

---

### Post by Bucky Ball on 2009-06-30
Yea, I liked it too but it kept opening itself whenever I opened a new page rather than just opening a tab and couldn't figure out how to change that.

---

### Post by AoSteve on 2009-06-30
I don't mind that personally.  Just firefox is so bloated for my ol' laptop here.  It's got some power to it, but still I don't like using more resources then I have to with it.  Simplicity is what I want and epiphany seems to be the lowest weight browser that fits my needs from the repos!  :)

---

### Post by Bucky Ball on 2009-06-30
I used one called Dillo for awhile. In the repos, you might like to try that if you haven't already.

---

### Post by AoSteve on 2009-06-30
I tried it, but it looks too much like a mobile browser to me.  EXTREMELY lightweight, but just not what I was looking for.  :)

---

