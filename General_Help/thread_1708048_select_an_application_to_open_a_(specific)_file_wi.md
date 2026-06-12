---
title: "select an application to open a (specific) file with"
date: 2011-03-16
forum: General Help
---

### Post by Lars_bylund on 2011-03-16
I have this problem, that I want a specific .exe file to open in Mono, but all other .exe files to open in Wine. 

However, the only option there is, are 'Select an application to open XXXX.exe and other files of type "DOS/Windows executable"' 

but I just want to open THIS .exe file in mono, and the rest in WINE.

I have been in similar situations before, in that I opened a folder containing music with VLC, and it worked fine, but after that, it assumed that I wanted to open all folders in VLC.

I assume that there must be an option for this, and I can not see why it ain't an option by default.

(I'm using Ubuntu 10.10)

---

### Post by antaios256 on 2011-03-16
when you select Open with other application. select the application you want to use, and on th bottom left of the windows there is a check box that says "remember this application for "XXXXXX type files" and just make sure it is unchecked it before you hit okay.

---

### Post by Lars_bylund on 2011-03-20
yes, but is there no way of making this specific .exe file remember to open with MONO instead of wine?

---

### Post by directhex on 2011-03-20
Nautilus isn't that smart. What's extra frustrating is that it's easy to tell the difference between the two:

```
directhex@dream:~$ /usr/lib/cli/binfmt-detector-cli /usr/lib32/wine/fakedlls/notepad.exe && echo "mono" || echo "windows"
windows
directhex@dream:~$ /usr/lib/cli/binfmt-detector-cli /usr/lib/tomboy/Tomboy.exe && echo "mono" || echo "windows"
mono
```

Honestly, just use a startup script rather than running the .exe directly. You can double-click the .sh in Nautilus to run it, and it only needs a "mono foo.exe" line in it

---

