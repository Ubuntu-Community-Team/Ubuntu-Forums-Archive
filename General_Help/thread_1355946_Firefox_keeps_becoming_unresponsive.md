---
title: "Firefox keeps becoming unresponsive"
date: 2009-12-15
forum: General Help
---

### Post by K-Kariya on 2009-12-15
I've been using firefox with no problems up until a little while ago. Lately it becomes unresponsive whenever I try to arrange my bookmarks(every time i do this, the whole thing just becomes unresponsive.) or loading certain pages. Has anyone else had a similar problem or does anyone know where I can find info regarding this issue?

---

### Post by philinux on 2009-12-15
Try running in safe mode, some addons/plugins are known to cause problems.

Close firefox. Open a terminal and use...

```
firefox -safe-mode
```

Se if that cures it. If so try disabling each addon in turn. Process of elimination.

---

### Post by lovinglinux on 2009-12-15
Since the problem occours when you modify bookmarks, then it's probably a database related issue. You should optimize Firefox databases. See the Database Optimization section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) for instructions.

---

### Post by K-Kariya on 2009-12-16
I installed sqlite3, but I don't know where the script directory is at..

---

### Post by lovinglinux on 2009-12-16
> **K-Kariya said:**
> I installed sqlite3, but I don't know where the script directory is at..

Just save it somewhere in your home and run it from there.

---

### Post by K-Kariya on 2009-12-17
"Then make it executable and run it from the terminal."...How do i make it an executable(i'm sorry i'm still kinad new to all of this)

---

### Post by K-Kariya on 2009-12-17
Oh. I also noticed that now instead of being called Firefox, the browser is now called "Shiretoko". Idk if this has anything to do with it, but now I can't log onto my work's website because it tells me I have to log in from a Firefox browser.

---

### Post by lovinglinux on 2009-12-18
> **K-Kariya said:**
> "Then make it executable and run it from the terminal."...How do i make it an executable(i'm sorry i'm still kinad new to all of this)

Right-click on it and select the file Properties. There is an option to make it executable there.

> **K-Kariya said:**
> Oh. I also noticed that now instead of being called Firefox, the browser is now called "Shiretoko". 

Shiretoko is just the unbranded development name. There are [hundreds of threads](http://www.google.com/search?q=Shiretoko+site%3Aubuntuforums.org) about this subject. 

> **K-Kariya said:**
> Idk if this has anything to do with it, but now I can't log onto my work's website because it tells me I have to log in from a Firefox browser.

Use [User Agent Switcher](https://addons.mozilla.org/en-US/firefox/addon/59) extension.

---

