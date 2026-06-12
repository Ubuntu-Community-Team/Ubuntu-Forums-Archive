---
title: "playing pc games on ubuntu?"
date: 2011-01-21
forum: General Help
---

### Post by kitoisara on 2011-01-21
can i play pc games on ubuntu since i dont have windows anymore i wanted to know if i can still play some of my pc games. and also how do i turn down the brightness on ubuntu i cant find a way to do it im still learning everything.

---

### Post by nogoodnamesleft on 2011-01-21
World of Warcraft runs under WINE - or at least it used to when I was playing it.

---

### Post by frotzed on 2011-01-21
> **nogoodnamesleft said:**
> World of Warcraft runs under WINE - or at least it used to when I was playing it.

It still does.

@ OP: In order to use a Windows program on Linux, you need to use WINE, which is a compatibility layer.  You can install it from the Ubuntu Software Center.  [This link]("https://help.ubuntu.com/community/Wine") may answer some of your more basic questions.

---

### Post by kitoisara on 2011-01-21
ohh ok thanks thats what i was referring to so i can play some warcraft again.

---

### Post by earthmeLon on 2011-01-21
[http://winehq.org](http://winehq.org)  Check this website's "Application Database" to see how other users have installed/fixed issues with common games.  It will help you successfully install almost any game.

Also, make sure you are using graphics drivers that support 3d acceleration with this command:

```
glxinfo | grep direct
```

You should get a response like
```
direct rendering: Yes
```

---

