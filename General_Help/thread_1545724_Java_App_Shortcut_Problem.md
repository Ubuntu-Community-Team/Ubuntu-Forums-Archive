---
title: "Java App Shortcut Problem"
date: 2010-08-04
forum: General Help
---

### Post by trentscott on 2010-08-04
I have a Java app that I downloaded (the .jnlp source file is in my  home folder). When I run the program, it places a shortcut on my desktop  with the name (jws_app_shortcut_1280012345798.desktop) but it isn't  actually a clickable icon. It looks like a file with information in it  (link to source file, application title, date, etc.). Is there any way I  can make it an actual icon?

Here's the contents of the .desktop file:

```
[Desktop Entry]
Version=1.0
Type=Application
Icon=/home/trenton/.java/deployment/cache/6.0/48/1889bfb0-4965f0e2.ico
Comment=OANDA fxGame GUI
Terminal=false
Categories=Applications;OANDA fxGame
Name=OANDA fxGame
Exec=/usr/lib/jvm/java-6-sun-1.6.0.20/jre/bin/javaws -localfile /home/trenton/.java/deployment/cache/6.0/19/5d393513-61974f85
Encoding=UTF-8
```

---

### Post by chopinhauer on 2010-08-04
> **trentscott said:**
> It looks like a file with information in it  (link to source file, application title, date, etc.). Is there any way I  can make it an actual icon?


It is an application launcher, just make it executable (via right click > Properties) and you can run the application by double clicking on it.

---

### Post by trentscott on 2010-08-04
> **chopinhauer said:**
> It is an application launcher, just make it executable (via right click > Properties) and you can run the application by double clicking on it.

BINGO!! Thank you ):P

---

