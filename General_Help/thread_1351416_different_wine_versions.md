---
title: "different wine versions?"
date: 2009-12-10
forum: General Help
---

### Post by eyelessfade on 2009-12-10
I have now two wine versions. 1.1.34 from winehq and my own patched 1.1.33 for Dragon Age.

But I get the following when I tries to use my own wine
```
wine client error:0: version mismatch 393/394.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?
```
I have used the following export to make it plain that I want to use version 1.1.33:
```

export WINEPREFIX=/home/user/.dragonage                                                
export WINESERVER=/home/user/software/wine/bin/wineserver                              
export WINELOADER=/home/user/software/wine/bin/wine                                    
export WINEDLLPATH=/home/user/software/wine/lib/wine/
```

and /home/user/software/wine/bin is in my path.

if I do /home/user/software/wine/bin/wine --version
I get 1.1.34 which is clearly wrong

---

### Post by eyelessfade on 2009-12-12
Anyone?

---

