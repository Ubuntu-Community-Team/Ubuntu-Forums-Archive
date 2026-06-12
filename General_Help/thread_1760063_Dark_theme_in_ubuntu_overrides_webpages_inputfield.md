---
title: "Dark theme in ubuntu overrides webpages inputfields"
date: 2011-05-16
forum: General Help
---

### Post by ububeginner on 2011-05-16
I'm running 10.10 and using a dark theme for my desktop. The only problem is that the theme seems to override web pages so that certain elements get the colors specified in the gnome theme and look really bad as a result. For instance the facebook login site that I enclosed a screenshot of.

Is this web designers fault to just not bother to specify colors for those elements on their sites? (btw, this site is also affected)
Is there any easy way to fix this?

I don't mind the address bar or the search box in firefox, but I think websites should look the same regardless of users appearance themes in their OS.

---

### Post by wojox on 2011-05-16
It's the web designer's fault. Add this to *~/.mozilla/firefox/.../chrome/userContent.css*


```
input {
    -moz-appearance: none !important;
    background-color: white;
    color: black;
}

textarea {
    -moz-appearance: none !important;
    background-color: white;
    color: black;
}

```

---

### Post by ububeginner on 2011-05-16
Thx, that worked for input fields. 
Any idea what to add to take care of dropdown menus, checkboxes, and radiobuttons?

---

### Post by wojox on 2011-05-16
Here is the link [User CSS (changing fonts, colors and other style)]("http://www.mozilla.org/unix/customizing.html#usercss")

---

### Post by ububeginner on 2011-05-17
Didn't find anything on dropdown lists or checkboxes, but thanks anyway.

---

