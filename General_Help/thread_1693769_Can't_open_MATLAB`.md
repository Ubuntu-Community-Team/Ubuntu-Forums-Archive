---
title: "Can't open MATLAB`"
date: 2011-02-23
forum: General Help
---

### Post by jezzyjez on 2011-02-23
Hi,

I have installed MATLAB on my university licence into my home folder.

The program ran once after installation but I now can't open it again (doesn't appear in applications, can't fine executable)

It is R2010a Matlab 7

Thanks in advance
Jez

---

### Post by 3Miro on 2011-02-23
You have to find the folder where you installed MATLAB. Then you can run it with:
```
/folder/with/MATLAB/bin/matlab
```

You can make a shortcut with that command yourself, although if you make a shortcut as opposed to using the terminal, you will have to give it the -desktop option:
```
/folder/with/MATLAB/bin/matlab -desktop
```

---

### Post by jezzyjez on 2011-02-23
Hero!

Thanks a lot been struggling with that for a while!

---

### Post by dubious5 on 2011-03-28
Thanks 3Miro I was also stuck on that. But for some reason the desktop command didnt add the shortcut. I had to right click applications >edit menus >new item then browse for ¨matlab¨ in the bin folder.

---

