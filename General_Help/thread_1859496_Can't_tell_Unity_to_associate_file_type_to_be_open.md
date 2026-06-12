---
title: "Can't tell Unity to associate file type to be opened with a particular application"
date: 2011-10-13
forum: General Help
---

### Post by entropy1 on 2011-10-13
I just installed 11.10 64-bit.  Then I installed texmaker.  How do I tell Unity that when I double-click on a .tex file, it should be opened with texmaker?

If I right-click on a .tex file, one of the options is to open it with texmaker.  However, if I select "Properties" and then the "Open With" tab, texmaker is not listed.  When I click on "Show other applications", texmaker is not there, and there is no option to browse for it, as I recall
there was in 10.10.

Any ideas?

---

### Post by crdlb on 2011-10-14
There is a problem with texmaker's .desktop file, see: [http://code.google.com/p/texmaker/issues/detail?id=316](http://code.google.com/p/texmaker/issues/detail?id=316)

As a workaround, you can copy /usr/share/applications/texmaker.desktop to ~/.local/share/applications/ and perform the edit mentioned in that bug report:
```
Exec=texmaker %U
```

---

### Post by entropy1 on 2011-10-14
Thank you crdlb.  Works great.  I just edited the original file (using sudo) with the change you suggested, and then texmaker showed up in the list of applications to open .tex files with.

Just used your idea to solve a similar problem with the ipe drawing editor.

---

### Post by elbocata on 2011-10-29
Thank you all!!

It worked for me too. Although I also edited /usr/share/applications/texmaker.desktop directly

---

### Post by PiHalbe on 2012-05-24
I used it for LaTeXila and hope to prevent Firefox from opening my .aup (Audacity) files via this method.

Thanks and cheers!

EDIT: Worked fine with Audacity and some other applications. Again: great work!

---

