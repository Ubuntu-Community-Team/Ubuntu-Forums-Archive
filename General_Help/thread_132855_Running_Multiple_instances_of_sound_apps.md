---
title: "Running Multiple instances of sound apps"
date: 2006-02-19
forum: General Help
---

### Post by Sirin on 2006-02-19
Hello, I have a problem with my sound. When I try to run two sound apps at once, the sound halts in one, but plays very nicely in the other. I can't get any sound driver (OSS, ALSA, that kind of stuff) to work in multiple apps at once. I can only use sound with one app at a time. Is there a way that I can fix this problem? :confused:

---

### Post by cronholio on 2006-02-19
Try this:

```
killall esd
```

Restart all sound applications. Does it work now?

---

### Post by Sirin on 2006-02-19
[QUOTE=cronholio]Try this:

```
killall esd
```

Restart all sound applications. Does it work now?[/QUOTE]

Unfortunately, no. BTW, is there a way to permanently fix this problem?

---

### Post by sande on 2006-02-19
Actually this is something inherent in Linux, only one application gets to have access to the sound devices. Dont exactly know the reason behind this.

---

### Post by cronholio on 2006-02-19
Killing esd used to help in Hoary. 

For Breezy, I just found that link and I'll try it now:

[http://www.ubuntuforums.org/showthread.php?t=101125](http://www.ubuntuforums.org/showthread.php?t=101125)

---

