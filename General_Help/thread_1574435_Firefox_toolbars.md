---
title: "Firefox toolbars"
date: 2010-09-14
forum: General Help
---

### Post by J V on 2010-09-14
I have a nice big screen now and I'd like to use firefox at its best... for this reason, all my buttons are on the same line. Sadly due to a small bug in firefox, the last item on the bookmarks menu is always hidden because of the search/location bar expanding... How would I shrink the bars to a lower size/make them fixed size?

I remember doing something that got it back to normal, but I don't remember what... (Although a less attractive way is to grow the window larger than my screens resolution, then maximize...

It looks like gtk is allocating the size correctly but assuming it's too small and using up that size with a tearoff... Bit of a grandfather paradox...

---

### Post by J V on 2010-09-15
Bump... what file contains the interface settings, I can do it from there...

---

### Post by lovinglinux on 2010-09-15
See [http://www.mozilla.org/unix/customizing.html](http://www.mozilla.org/unix/customizing.html)

---

### Post by J V on 2010-09-15
That looks handy and it might work well, but the current "Settings" have my window set way too large, I need to find out where the *current* settings are (There is no userchrome.css in my profile)

The quickest way to do this would be to make the bookmarks toolbar expand (Or better, make gtk.toolbar.show-arrow false)

---

### Post by J V on 2010-09-16
bump

---

### Post by lovinglinux on 2010-09-16
> **J V said:**
> That looks handy and it might work well, but the current "Settings" have my window set way too large, I need to find out where the *current* settings are (There is no userchrome.css in my profile)

The quickest way to do this would be to make the bookmarks toolbar expand (Or better, make gtk.toolbar.show-arrow false)

You need to rename the file ~/.mozilla/firefox/<profilename>/chrome/userChrome-example.css to userChrome.css.

You might wanna try [Stylish]("https://addons.mozilla.org/en-US/firefox/addon/2108/") too.

---

### Post by J V on 2010-09-16
Right, but this still isn't helping... The only thing I can do is grap the gtklib files (Or are they compiled in? Nooo!) and switch that one little boolean...

---

### Post by lovinglinux on 2010-09-16
> **J V said:**
> Right, but this still isn't helping... The only thing I can do is grap the gtklib files (Or are they compiled in? Nooo!) and switch that one little boolean...

The userChrome.css by utself doesn't do anything. You need to add your own css styles. I don't know a style to do what you want.

---

### Post by J V on 2010-09-17
Found it:
```
#bookmarksBarContent .bookmark-item {visibility: visible !important;} 
```Now all I need is something to make the bugged tearoff go away :D

Got that too:
```
#bookmarksBarContent {min-width: 435px !important;} /* Insert own min-width, make sure it's an absolute width */
```

---

### Post by lovinglinux on 2010-09-17
> **J V said:**
> Found it:
```
#bookmarksBarContent .bookmark-item {visibility: visible !important;} 
```Now all I need is something to make the bugged tearoff go away :D

Got that too:
```
#bookmarksBarContent {min-width: 435px !important;} /* Insert own min-width, make sure it's an absolute width */
```

Cool.

---

### Post by adf88 on 2011-03-24
Another workaround is to add a separator at the end. The separator will be hidden instead of the last bookmark item. Not a perfect solution but quick and easy and can be applied by anyone.

---

