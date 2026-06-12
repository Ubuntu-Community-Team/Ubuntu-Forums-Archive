---
title: "Big mouse cursors &gt;.&lt;"
date: 2012-03-06
forum: General Help
---

### Post by farukdgn on 2012-03-06
I want to get rid of ubuntu issues. I have big cursors now. I clicked something from the up right corner when I was about to install Ubuntu, then mouse cursor and texts got bigger. I couldn't disable it and now cursor is still big >.<
[IMG]http://img210.imageshack.us/img210/2219/screenshotfrom201203061.png[/IMG]

---

### Post by raja.genupula on 2012-03-06
change the theme from appearance settings will may effect the change of mouse . but whats this big text ?please give us more info .

---

### Post by stinkeye on 2012-03-06
To get the current size of the mouse cursor. (default is 24)
```
gsettings get org.gnome.desktop.interface cursor-size 
```



To reset to 24
```
gsettings reset org.gnome.desktop.interface cursor-size
```

---

