---
title: "sk1 not showing up on the application list"
date: 2010-02-22
forum: General Help
---

### Post by dosox on 2010-02-22
Forgive me if I posted this on the wrong forum

I installed sk1 .deb file from the sk1's site.. Everything went well but it doesn't show up on my application list.

And when i type sk1 on the terminal it shows this:

doson@DOSOX:~$ sk1
error opening file /usr/share/fonts/truetype/ttf-symbol-replacement/symbol-replacement.ttf
error opening file /usr/share/fonts/truetype/ttf-tahoma-replacement/tahoma-replacement.ttf
error opening file /usr/share/fonts/truetype/ttf-tahoma-replacement/tahomabd-replacement.ttf
error opening file /usr/share/fonts/truetype/ttf-symbol-replacement/symbol-replacement.ttf
error opening file /usr/share/fonts/truetype/ttf-tahoma-replacement/tahoma-replacement.ttf
error opening file /usr/share/fonts/truetype/ttf-tahoma-replacement/tahomabd-replacement.ttf
shared memory images supported
Cairo surfaces are initialized!


Can you help me?

---

### Post by gmargo on 2010-02-22
Try installing these packages:

[LIST]
[*]ttf-symbol-replacement
[*]ttf-tahoma-replacement
[/LIST]
Oh, that's strange.  The package list for the tahoma one says the files are
```

/usr/share/fonts/truetype/ttf-tahoma-replacement/tahoma-replacement.ttf/tahoma.ttf
/usr/share/fonts/truetype/ttf-tahoma-replacement/tahomabd-replacement.ttf/tahomabd.ttf

```which is not quite what your program was looking for.  So perhaps you have the fonts installed already but the sk1 program is mangling the path (stopping at the first .ttf it found).

The other alternative is to install the **msttcorefonts** package to get the Microsoft fonts.

---

### Post by dosox on 2010-02-23
> **gmargo said:**
> Try installing these packages:

[LIST]
[*]ttf-symbol-replacement
[*]ttf-tahoma-replacement
[/LIST]
Oh, that's strange.  The package list for the tahoma one says the files are
```

/usr/share/fonts/truetype/ttf-tahoma-replacement/tahoma-replacement.ttf/tahoma.ttf
/usr/share/fonts/truetype/ttf-tahoma-replacement/tahomabd-replacement.ttf/tahomabd.ttf

```which is not quite what your program was looking for.  So perhaps you have the fonts installed already but the sk1 program is mangling the path (stopping at the first .ttf it found).

The other alternative is to install the **msttcorefonts** package to get the Microsoft fonts.
btw Is this a major issue :D

---

### Post by dosox on 2010-02-23
oh btw I found this [link]("http://pythonide.blogspot.com/2009/05/sk1-vector-graphics-editor-is-now.html") and it says 

... . The packaging is not perfect yet. For example there will be no entry in the start menu. This will be fixed in a next release. I've sent Igor from sK1 the necessary files to resolve this issue. So for now start sK1 by typing "sk1" in the run dialog (Alt+F2) or in a terminal.

---

