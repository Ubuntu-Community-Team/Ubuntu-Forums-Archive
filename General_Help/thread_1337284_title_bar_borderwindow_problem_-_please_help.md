---
title: "title bar border/window problem - please help"
date: 2009-11-25
forum: General Help
---

### Post by renebs on 2009-11-25
Hi,

The title bar/Borders on all windows under gnome have vanished. 
I read and tried many solutions from these 4 threads:
[http://ubuntuforums.org/showthread.php?t=1116022](http://ubuntuforums.org/showthread.php?t=1116022)
[http://ubuntuforums.org/showthread.php?t=1212338](http://ubuntuforums.org/showthread.php?t=1212338)
[http://ubuntuforums.org/showthread.php?t=920875](http://ubuntuforums.org/showthread.php?t=920875)
[http://ubuntuforums.org/showthread.php?t=875741](http://ubuntuforums.org/showthread.php?t=875741)

Basically, I do not have Emerald installed, I do have compiz, and it did had a different parameter/option under window decorator, so I changed it
```

from: /usr/bin/compiz-decorator
to: gtk-window-decorator --replace 
```

Note that if I run gtk-window-decorator --replace it doesn't do any good, in fact here is the output while running it on xterm:

```
~$ gtk-window-decorator --replace 
gtk-window-decorator: symbol lookup error: gtk-window-decorator: undefined symbol: decor_blend_border_picture
```

If I run $ metacity --replace I do have some title bar and borders back, however the effect disappear after a reboot (if compiz is working, with NO effect - i.e. choosing None under Visual Effects - it works fine), hence that's why I think such solution could be a bit better than that, i.e. using Compiz and having title bars/borders

This problem started after I have installed Enlightenment e17, I imagine it might have changed some config parameter that gnome(or gtk-window-manager) didn't like it. So it shouldn't be a problem to fix it, I just need help to find where is the error.

---

