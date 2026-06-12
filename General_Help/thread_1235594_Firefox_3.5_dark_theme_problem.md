---
title: "Firefox 3.5 dark theme problem"
date: 2009-08-09
forum: General Help
---

### Post by akudewan on 2009-08-09
I upgraded to Firefox 3.5 *Shiretoko* today. The address bar drop-down doesn't seem to be getting along my current desktop theme.

[IMG]http://imgur.com/hbOpX.png[/IMG]

Can someone help me fix this? Ideally, I'd like the blue links to appear in white or any lighter shade.

---

### Post by Rob_H on 2009-08-09
You could modify the theme yourself. Theme files are usually located in **~/.mozilla/firefox/<profile_dir>/extensions**. Or, what I often do is use a light theme, but then switch the whole window to dark using the Negative plugin of Compiz. This has the benefit of switching the web page contents as well, often making it easier to read. The result is surprisingly good most of the time. Here's a screenshot of my reply.

---

### Post by caish5 on 2009-08-09
There seems to be a difference in how 3.5 renders themes vs 3.0.
The Dust theme included in ubuntu does this too.
Really annoying.
I like dust but i hate that

---

### Post by akudewan on 2009-08-10
I figured that I could use the userChrome.css file to change the  colors. But I can't figure out the CSS classes that firefox uses for the location-bar dropdown background and I can't find any documentation.

For the time being, I'm using a theme that uses better colors for the location bar. But it is by no means perfect.
[IMG]http://imgur.com/akCyr.png[/IMG]

---

### Post by mcduck on 2009-08-10
> **caish5 said:**
> There seems to be a difference in how 3.5 renders themes vs 3.0.
The Dust theme included in ubuntu does this too.
Really annoying.
I like dust but i hate that

This is because Firefox doesn't actually directly use GTK but XUL instead. It's ability to use your GTK theme is kind of a hack and not perfect, dark themes are known to be problematic.

Actually most dark themes include instructions how to use Firefox's usercontent.css file to fix the problems. If the instructions were not included with the theme package itself make sure to check the page where you downloaded the theme..

---

### Post by caish5 on 2009-08-10
I'm just using the dust theme included with jaunty. It used to work fine with firefox 3.0

---

