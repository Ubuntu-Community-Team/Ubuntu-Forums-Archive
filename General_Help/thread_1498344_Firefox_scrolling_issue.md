---
title: "Firefox scrolling issue"
date: 2010-05-31
forum: General Help
---

### Post by Edwinem on 2010-05-31
After installing a bunch of new updates with the update manager a few problems have popped up regarding the scrolling in firefox with the arrow keys. The first problem is that when I open up a new web page it does not automatically allow me to scroll. I have to first click the web page and then are the arrow keys enabled. The second problem that I have is that when I press the down arrow key to scroll down in the beginning it jumps down to the end of the page. The third and final problem is how it scrolls. For some reason a site in firefox acts like a word document. Instead of be the arrow keys controlling the scroll bar it controlls the little I symbol you see when typing.

If anybody has a quick fix for this it would be really appreciated. It is amazing how annoying it can be when you can't scroll with the arrow keys. If nobody knows how to then I will probably just reinstall firefox.

Edit: I have also just figured out that page up and down also do not work.

---

### Post by cariboo on 2010-05-31
You may have a corrupt firefox profile. To create a new on, press Alt-F2 and type:

```
firefox -Profilemanager
```

If that works, just transfer your bookmarks from the old profile.

---

### Post by lovinglinux on 2010-05-31
> **cariboo907 said:**
> You may have a corrupt firefox profile. To create a new on, press Alt-F2 and type:

```
firefox -Profilemanager
```

If that works, just transfer your bookmarks from the old profile.

If you want to transfer more than just the bookmarks, see [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html).

You could also try to identify where the problem is, instead of creating a new profile. Then see [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

