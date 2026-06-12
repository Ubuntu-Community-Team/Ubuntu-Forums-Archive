---
title: "fail to update ubuntu"
date: 2009-10-30
forum: General Help
---

### Post by Mesqueeb on 2009-10-30
Heya!
When I press on "check for updates" it says:

Failed to fetch [http://archive.ubuntulinux.jp/ubuntu-ja/dists/Intrepid/Ibex//binary-i386/Packages.gz](http://archive.ubuntulinux.jp/ubuntu-ja/dists/Intrepid/Ibex//binary-i386/Packages.gz)  404 Not Found [IP: 121.119.163.196 80]
Some index files failed to download, they have been ignored, or old ones used instead.

can anyone help me?&#12288;Thanks!

-Mesqueeb

---

### Post by Mesqueeb on 2009-10-31
now it`s giving me problems in firefox, telling my I can't search things on google anymore.

I&#12288;searched things like:
"I just want to search google" or something and it gives me message:

ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],alias)
5:()
6:SRCH_SVC_getEngineByAlias(I)
7:getEngineByAlias(I)
8:getShortcutOrURI(I just want to search on google,[object Object])
9:canonizeUrl([object KeyboardEvent],[object Object])
10:handleURLBarCommand([object KeyboardEvent])
11:anonymous(textentered,[object KeyboardEvent])
12:fireEvent(textentered,[object KeyboardEvent])
13:onTextEntered()


........

can anyone help me? THANKS!&#12288;^^

---

### Post by Mesqueeb on 2009-11-02
bump

---

### Post by Mesqueeb on 2009-11-04
bump

---

### Post by grandtoubab on 2009-11-04
in terminal

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

```
sudo apt-get dist-upgrade
```

---

### Post by wilee-nilee on 2009-11-04
Can you get on the net? If so you might just go to software sources in preferences and click other in the 1st tabs dropdown then best server.

---

