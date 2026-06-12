---
title: "How can I draw progressbar for my bash scripts...."
date: 2010-05-12
forum: General Help
---

### Post by wrix on 2010-05-12
Hello, i am using Kubuntu 9.04 with KDE4 installed. I created some bash scripts and used Kdialog to display the graphical items and other things, only the progressbar in Kdialog, I am unable to use. I read the tutorial in KDE's website but still it shows me an error saying "ERROR: Couldn't attach to DCOP server!". Please help me in this regards, I want to draw the progressbar in my bash scripts. Thanks.

---

### Post by Zorael on 2010-05-17
Whatever tutorial you're reading, it was written for KDE3. DCOP was deprecated in favor of [url=http://en.wikipedia.org/wiki/D-Bus[/url].

```
#! /bin/bash

ref=$(kdialog --title "Title" --progressbar "(starting up)" 15)

qdbus $ref Set org.kde.kdialog.ProgressDialog maximum 3
qdbus $ref Set org.kde.kdialog.ProgressDialog value 1
qdbus $ref setLabelText "here we go"
sleep 3
qdbus $ref Set org.kde.kdialog.ProgressDialog value 2
qdbus $ref setLabelText "almost done"
sleep 3
qdbus $ref Set org.kde.kdialog.ProgressDialog value 3
qdbus $ref setLabelText "yay!"
sleep 1
qdbus $ref close
```

Use qdbusviewer (or tab completion with qdbus) to see the qdbus interface of kdialog.ProgressDialog. Or see the attached screenshot.

Properties must be Set, methods can be called normally.

---

