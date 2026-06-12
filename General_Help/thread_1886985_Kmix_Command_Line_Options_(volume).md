---
title: "Kmix Command Line Options (volume)"
date: 2011-11-26
forum: General Help
---

### Post by ReptilianShadow on 2011-11-26
I'm wondering if anyone knows how to raise/lower master volume in Kmix via command line?

I want to bind volume down/up to different keys but, I didn't see an option to change volume keyboard shortcuts anywhere in default system settings. (Shortcuts and Gestures)

I also checked man kmix (nonexistent). As well as kmix --help-all, no obvious volume options there, as far as I can see.

So, anyway to lower global volume in kde/kmix vis command or script?

Any input is appreciated, Thanks.

---

### Post by ReptilianShadow on 2011-11-26
Alright, managed to figure it out.
Hopefully this helps someone else.

Used qdbus:
Increase Volume:
```
qdbus org.kde.kmix /kmix/KMixWindow/actions/increase_volume com.trolltech.Qt.QAction.trigger
```

Decrease Volume:
```
qdbus org.kde.kmix /kmix/KMixWindow/actions/decrease_volume com.trolltech.Qt.QAction.trigger
```

Mute Volume:
```
qdbus org.kde.kmix /kmix/KMixWindow/actions/mute com.trolltech.Qt.QAction.trigger
```

Made custom keyboard shortcuts for all, and all seem to work just fine.

Sources:
[http://permalink.gmane.org/gmane.linux.suse.kde/12847](http://permalink.gmane.org/gmane.linux.suse.kde/12847)

---

### Post by Bonster on 2011-11-27
Should be in 
System Settings > Shortcuts And Gestures > Global Keyboard Shortcuts > KDE component > Kmix

then just change the hotkeys you want

---

