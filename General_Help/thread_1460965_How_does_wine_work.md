---
title: "How does wine work?"
date: 2010-04-23
forum: General Help
---

### Post by JustSomeGuy805 on 2010-04-23
Do you have to install windows to your hard drive first? If so, does windows need to be activated?  Or does wine do everything like an emulator?

---

### Post by doas777 on 2010-04-23
no, wine does not involve anything from MS (unless a program you want to run in wine requires a native dll, but that is getting ahead of things). 
wine is kind of like a virtual windows system within your home directory, but there is no gui that you would see (no desktop or windows or anything like that).

once you have wine installed, you can install windows programs into wine with a command like:
```

wine <path-to-installer>

```

or if the app has no installer, just run it like 'wine <pathtoexe>'

here is some good info:
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by jerome1232 on 2010-04-23
Wine translates Windows api calls into Linux ones. It's not an emulator per say but you can think of it as one.


It doesn't have any micrsoft code in it and does not require you have a real copy of Windows. In some cases real windows libraries can be used to get wine working with specific software.

[http://www.winehq.org/about/](http://www.winehq.org/about/) If you poke around there's some explanantions about what wine is here.

---

### Post by JustSomeGuy805 on 2010-04-24
thanks for the replies guys.:)

---

