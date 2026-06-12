---
title: "Pandora makes Firefox freeze up and give unresponsive script errors."
date: 2011-11-21
forum: General Help
---

### Post by rectec794613 on 2011-11-21
Hello, guys. Here's what I'm using:

-Firefox 7.0.1 (EDIT - just updated to 8.0, no dice. :()
-Kubuntu 11.10 (Fully updated)

Gonna make this more structured this time, to enhance understanding.

[Intro]
I've been listening to Pandora since 2009 and have had no problems with it up until a month or two ago. The recent change to HTML5 was a problem because it continuously  took up massive amounts of memory, but now I have a bigger problem.

[Problem]
If I go to Pandora, I am always signed out, and I always get presented with the "login" screen. When I sign in, it takes me to a blank page with only Now playing, music feed, etc. at the top. If I click on one of them, nothing will happen. At the login screen, I can click a genre down below, and it will play. However, if I try to sign in or use the player's controls, it completely freezes. I should mention that most if not all times it freezes, I get saved by an Unresponsive Script error. The scripts are usually along the lines of "http://_[www.pandora.com/script.combined.js](www.pandora.com/script.combined.js)_?v=319213114:56". Please don't try to read the whole code :)

[Narrowing Down]
-I have no problems like this on Windows (Which is why I like to keep it around : P). 
-I have started Firefox in safe mode, but it didn't help
-I purged Firefox, deleted it's home folder settings (.mozilla), and reinstalled it, but Pandora still wouldn't work.
-It works fine on Chromium and Rekonq
Hopefully we can narrow it down to a problem specifically on KDE with Firefox.

Any questions you may have regarding this issue, feel free to ask. Thanks in advance.

---

### Post by rectec794613 on 2011-11-22
Anybody?

---

### Post by Historian1776 on 2011-11-23
I'm having the same issues running both firefox 7.0.1 or firefox 8. It works with the chromium browser. Must be a firefox issue with ubuntu. Firefox and pandora work fine on windows boxes.

---

### Post by Historian1776 on 2011-11-23
Someone else has already solved it, and it worked for me. Here's the link to the other thread. [http://ubuntuforums.org/showthread.php?t=1663230](http://ubuntuforums.org/showthread.php?t=1663230) Download the flash-aid add-on for firefox, then click on the new icon next to your "home" button on your toolbar. Run that with defaults and it cleans up a bunch of leftover and conflicting junk from adobe. Works like a charm. 

Hope this helps.

---

### Post by rectec794613 on 2011-11-23
Works perfectly! It's all back to normal, and the optimizations that the addon does are great. Thank you!

---

