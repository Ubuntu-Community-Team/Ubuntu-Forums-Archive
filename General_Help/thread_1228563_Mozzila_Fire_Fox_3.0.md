---
title: "Mozzila Fire Fox 3.0"
date: 2009-08-01
forum: General Help
---

### Post by CaseSensative on 2009-08-01
ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1)
2)
3)
4:epsGetAttr([object Object],alias)
5)
6:SRCH_SVC_getEngineByAlias([http://google.com/](http://google.com/))
7:getEngineByAlias([http://google.com/](http://google.com/))
8:getShortcutOrURI([http://google.com/](http://google.com/),[object Object])
9:canonizeUrl([object MouseEvent],[object Object])
10:handleURLBarCommand([object MouseEvent])
11nclick([object MouseEvent])

I receive this error when using Fire Fox, I am forced to use Opera. Not that Opera is bad I just am used to fire fox. Any help would be appreciated.

---

### Post by darolu on 2009-08-01
I would recommend reinstalling firefox:
```
sudo apt-get install --reinstall firefox
```
You can try installing another browser or application that uses xulrunner/gecko like epiphany or liferea (news feed reader):
```
sudo apt-get install epiphany liferea
```

Additionally you can install firefox 3.5:
```
sudo apt-get install firefox-3.5
```

---

### Post by CaseSensative on 2009-08-01
I reinstalled Mozzila 3.0 and that didn't work, but I installed 3.5 and it does work. That seems pretty weird to me. Is there anything I could have done to corrupt a file or something?

---

