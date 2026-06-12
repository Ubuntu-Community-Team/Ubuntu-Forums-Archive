---
title: "Firefox new tab = Screen flickers"
date: 2009-11-18
forum: General Help
---

### Post by detroit/zero on 2009-11-18
I have an issue where opening a new tab in Firefox cause the screen to black out for a split second - or, to put it another way, the screen flickers once and then works normally.

It only does it when there's no other tabs open, and I suspect it has something to do with drawing of the tab bar (which I have set to disappear when only the main window is open). It does also do it when I close the last tab and the bar disappears.

I have Firefox 3.5.5, and am running Karmic with all current updates.

---

### Post by londy on 2009-11-27
Did you find a solution?

I'm not sure if it's the same problem but I'm also experiencing the same split-second "flickers" occasionally when I open a new tab. It's not a big deal but it is a little annoying.

I have a fresh install of Kubuntu Karmic with Firefox 3.5.5.

---

### Post by roharme on 2009-11-27
Update your Video driver.
 
I had similar problem in Windows.
 
fixing the driver version did the trick

---

### Post by detroit/zero on 2009-11-27
> **roharme said:**
> Update your Video driver.
> **detroit/zero said:**
> I have Firefox 3.5.5, and am running Karmic with **all current updates.**
> **londy said:**
> Did you find a solution?

I'm not sure if it's the same problem but I'm also experiencing the same split-second "flickers" occasionally when I open a new tab. It's not a big deal but it is a little annoying.

I have a fresh install of Kubuntu Karmic with Firefox 3.5.5.

Nope. Haven't yet found a solution.

One thing I have noticed is that the full-screen flicker only happens when the FF window is maximized. If FF isn't maximized, and FF is whatever random sized, the flicker is contained within the FF window.

That's what leads me to believe, roharme, that it's not necessarily a driver issue since the issue is application specific - only FF does this, not even other apps that I run fullscreen and use tabs, like gedit for example.

---

### Post by audiomick on 2009-11-27
Haven't read this through, but it might have something for you:
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by detroit/zero on 2009-11-27
Holy cow! That's a big post.

---

### Post by aperomsik on 2009-12-06
I have this problem too. I had it differently in older versions and fixed it with some kind of change to bookmarks of all things. I don't remember what it was. But now it seems to happen when opening a new tab, possibly only tabs for which FireFox shows a message above, such as "remember this password?" or "prevented a popup." If I switch to another tab and switch back it is usually OK until I open another tab... or dismiss the above-message.

---

### Post by detroit/zero on 2009-12-06
> **aperomsik said:**
> I have this problem too. I had it differently in older versions and fixed it with some kind of change to bookmarks of all things. I don't remember what it was. But now it seems to happen when opening a new tab, possibly only tabs for which FireFox shows a message above, such as "remember this password?" or "prevented a popup." If I switch to another tab and switch back it is usually OK until I open another tab... or dismiss the above-message.
I don't see it in relation to the drop-down notifications in the FF window - quite the contrary, for me, those work nicely.

For me, what I'm talking about is either opening the first new tab or getting rid of the second-to-last tab, which causes either the appearance or disappearance of the tab bar. Because vertical real estate is at a premium on laptops, I don't care to have the tab bar there when I don't have multiple tabs open. Every time the tab bar comes or goes, the inside of my FF window blinks out and back.

---

### Post by aperomsik on 2009-12-06
> **detroit/zero said:**
> 
For me, what I'm talking about is either opening the first new tab or getting rid of the second-to-last tab, which causes either the appearance or disappearance of the tab bar. 

I almost never have only one tab open. On my work machine (running FF3.5 for Solaris) I have 36 tabs open at the moment. But anyway, by any chance do you have the FireBug add-on installed? I just noticed that if I hit F12 to summon or dismiss the FireBug panel, that tab flickers until I switch to another tab and switch back. 

Does switching to the other tab and switching back help you? If not I guess the two flickers are unrelated.

---

### Post by detroit/zero on 2009-12-06
> **aperomsik said:**
> But anyway, by any chance do you have the FireBug add-on installed? 
[...]
Does switching to the other tab and switching back help you? If not I guess the two flickers are unrelated.
Nope, no firebug here. My add-ons are pretty slim: NoSquint, TabScope, Customize Google, and that's about it.

---

