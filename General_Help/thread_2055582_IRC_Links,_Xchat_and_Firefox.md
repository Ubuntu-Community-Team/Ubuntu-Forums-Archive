---
title: "IRC Links, Xchat and Firefox"
date: 2012-09-09
forum: General Help
---

### Post by Blasphemous on 2012-09-09
Thanks to this tutorial - [http://ubuntuforums.org/showthread.php?t=25372](http://ubuntuforums.org/showthread.php?t=25372) - I was able to **associate IRC links** - the links I usually find on the intenet are mostly like irc://xxxxxxxx.net - **to xchat **when I click on them while surfing in Firefox: now, when I click on a link in the browser, xchat* starts up* and *shows me a list of channels *- like #Debian #Ubuntu #Firefox ecc ecc-
BUT
**it does not connect to that particular channel I clicked before.**

It seems like I got to associate that kind of file with xchat, but when I click on a link the client does not open that link, it just starts as normal.

:(

---

### Post by d3v1150m471c on 2012-09-09
real men use irssi

---

### Post by Blasphemous on 2012-09-10
Solved!

Open Terminal
Type:
```
 sudo gedit /usr/bin/xchat-firefox
```

Copy and paste this code
```
#!/bin/bash
xchat --existing --url=$@
```
Save

Open terminale and type
```
 sudo chmod +x /usr/bin/xchat-firefox
```

Launch **Firefox**
Preferences > Application and search for "*IRC*"
In the menu click on "*Other*" and than browse to* /System/usr/bin* and select xchat-firefox
Save and exit

Everything should work :) ;)

---

