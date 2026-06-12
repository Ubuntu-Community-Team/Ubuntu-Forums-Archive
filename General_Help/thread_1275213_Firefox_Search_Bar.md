---
title: "Firefox Search Bar"
date: 2009-09-25
forum: General Help
---

### Post by GO%)$@*1 on 2009-09-25
There is a bar on my search bar. I don't know how to get rid of it...

---

### Post by mac9416 on 2009-09-25
Have you tried View > Toolbars > Customize and dragging the undesired element off of the toolbar? (assuming that that is its own element)

---

### Post by GO%)$@*1 on 2009-09-25
Yeah, and in the element selection window, it appears with a bar on it, too.

---

### Post by lovinglinux on 2009-09-25
I'm not sure, but it looks like there are too many elements on the toolbar and the last one does not have enough space. Try to remove some elements like spaces, to see if that thing expands into something useful.

You can also reset the toolbar to it's original state from the customization window. That should fix any problem, if you don't mind customizing it again.

---

### Post by GO%)$@*1 on 2009-09-25
Nope. That didn't work, either.

---

### Post by lovinglinux on 2009-09-25
> **kuyanatan said:**
> Nope. That didn't work, either.

Could you post a screenshot of your entire Firefox screen and draw some arrows pointing to the problems? Also, which theme are you using?

---

### Post by GO%)$@*1 on 2009-09-25
> **lovinglinux said:**
> Could you post a screenshot of your entire Firefox screen and draw some arrows pointing to the problems? Also, which theme are you using?

Here it is. Using [theme Foxdie 3.9.1 Blue.]("http://foxdie.us/")

---

### Post by lovinglinux on 2009-09-25
> **kuyanatan said:**
> Here it is. Using [theme Foxdie 3.9.1 Blue.]("http://foxdie.us/")

Could be a theme issue. Have you tried another theme to see if the same problem occurs?

---

### Post by GO%)$@*1 on 2009-09-26
> **lovinglinux said:**
> Could be a theme issue. Have you tried another theme to see if the same problem occurs?
It looks like it was the theme. Do you know how  I could report this to the person who made the theme, or a possible fix?

---

### Post by GO%)$@*1 on 2009-09-26
It turns out it was a conflict between a Stylish script and my theme. The stylish script is at [http://userstyles.org/styles/3292](http://userstyles.org/styles/3292). Is there a way I can modify that script so that it will work with my theme?

Stylish script code:
```
@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
.search-go-button { display: none !important; }
.search-button-stack { display: none !important; }
#go-button { display: none !important; }
```

---

