---
title: "Keepassx does not show up in the Unity bar"
date: 2012-05-31
forum: General Help
---

### Post by bobzr on 2012-05-31
Keepassx does not show up in the Unity bar when it is running and is lost when another application opens. Only way to get it back on sight is to hit Win+W and show all the active windows.
Does anybody knows any workaround, hoping that this bug will be fixed soon?

[Usinig Ubuntu 12.04 64-bit, no such problem with previous versions]

---

### Post by stinkeye on 2012-06-01
This worked for me.
Unlock your current keepassx launcher if you have one.
After starting keepassx from the dash and entering your password, minimize keepassx.
restart compiz...alt+F2
```
compiz --replace
```
and it should now show in the launcher.
Lock it to the launcher and it should show with subsequent launchings and minimizing.

---

### Post by bobzr on 2012-06-01
> **stinkeye said:**
> This worked for me.
Unlock your current keepassx launcher if you have one.
After starting keepassx from the dash and entering your password, minimize keepassx.
restart compiz...alt+F2
```
compiz --replace
```
and it should now show in the launcher.
Lock it to the launcher and it should show with subsequent launchings and minimizing.

Thanks for the tip. I've tried it and it works, but unfortunately only once. When I restart my session I have to repeat that again, and again... :(

---

### Post by bobzr on 2012-06-01
OK I found a workaround that seems to be working for me on Ubuntu 12.04. Here's what I did:

Uninstall keepassx.

Make sure to have qt4 libs and g++ installed:

```
sudo apt-get install libqt4-core libqt4-dev libxtst-dev
sudo apt-get install g++
```

Download the sourcecode from the official site.
Extract the files and change into the directory.
Compile keepassx from the sourcecode:

```
qmake-qt4
make
sudo make install
```

Reboot. Extracted folder can be removed.

Enjoy Keepassx
;)

---

