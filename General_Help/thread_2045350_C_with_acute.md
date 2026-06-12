---
title: "C with acute"
date: 2012-08-21
forum: General Help
---

### Post by MountainLion37 on 2012-08-21
How do I type a c with acute in Ubuntu 12.04? AltGr-; C gives me a c with cedilla instead. My keyboard layout is the English UK default. There are a few solutions posted, but they are all for Gnome 2, and I don't have the specified files.

---

### Post by col48 on 2012-08-21
I don't know the answer, but have you tried AltGr= then c?

In 10.04, AltGr; then c gives &#263; as you describe and AltGr= then c gives ç
(I have UK English configuration).

Because maybe they are swapped around?

---

### Post by MountainLion37 on 2012-08-21
No, they both give c-cedilla.

---

### Post by col48 on 2012-08-21
Looks like you're not alone.  See this...

[https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/919899](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/919899)

I assume the 'compose' key referred to is what we have called 'AltGr'.

---

### Post by col48 on 2012-08-21
I was wrong about 'compose'.

see

[http://wiki.linuxquestions.org/wiki/Accented_Characters](http://wiki.linuxquestions.org/wiki/Accented_Characters)

for some ideas.  This might provide you with a way through, or at least a workaround.

but this looks like it could point to a proper answer.

[http://www.linuxquestions.org/questions/linux-desktop-74/problem-creating-custom-xkb-layout-605568/](http://www.linuxquestions.org/questions/linux-desktop-74/problem-creating-custom-xkb-layout-605568/)

although I imagine a software upgrade may at some point do the job differently.

---

### Post by MountainLion37 on 2012-08-21
Figured out exactly what's happening. The US-International layout in Windows has c-cedilla on the same key as the acutes, and many Brazilian users complained that they had to use a specific dead key for the cedilla. However, now there is no way to type the c-acute, which I need rather frequently.
This problem was addressed in thread [1122090]("http://ubuntuforums.org/showthread.php?t=1122090"), but I don't have the libgtk-2.0-0.immodules file or anything else mentioned in the thread for that matter...

---

### Post by spjackson on 2012-08-21
Ctrl+Shift+u followed by 0107<Enter> seems to work.

---

### Post by MountainLion37 on 2012-08-21
> **spjackson said:**
> Ctrl+Shift+u followed by 0107<Enter> seems to work.
Thanks. I forgot about the Unicode input. 
But I'll leave the question open, in case there is some configuration file I can change to do it more quickly.

---

