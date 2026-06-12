---
title: "Endnote X3 with wine"
date: 2010-10-06
forum: General Help
---

### Post by unnilennium on 2010-10-06
Hello,

I have successfully installed endnote x3 running under wine thanks to this document : [http://www.docstoc.com/docs/23936524/EndNote-on-Linux](http://www.docstoc.com/docs/23936524/EndNote-on-Linux)

and thanks to winetricks to complete the dll requirement that endnote was asking on startup.

Nos i have two problems:

1/ i am not able to open pdf document linked into the database, i have this error:
```
This URL (\\Z:\media\sda5\path\to\JPP.data\PDF\author2008-1341524334\author2008.pdf) could not be launched
```



2/I have some issues with the left panel : all text are big black line instead of words (see attachment)

---

### Post by colferma on 2010-10-18
bump!

---

### Post by unnilennium on 2010-10-30
Solved this issue with :

```

sh winetricks riched20 riched30
```

thanks to  [http://readlist.com/lists/winehq.org/wine-users/3/19700.html](http://readlist.com/lists/winehq.org/wine-users/3/19700.html)
and 
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=4614684](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=4614684)


Winetricks script is really the one you need to execute for this kind of problem

---

### Post by unnilennium on 2010-10-30
Now if you want to open your pdf attached files inside you favorite linux app :

[http://wiki.winehq.org/FAQ#head-e03d797155ac6e9d8176f045acbdeebc28ad33d4](http://wiki.winehq.org/FAQ#head-e03d797155ac6e9d8176f045acbdeebc28ad33d4)

or

[http://www.winehq.org/pipermail/wine-users/2008-June/036336.html](http://www.winehq.org/pipermail/wine-users/2008-June/036336.html)


personnaly i have done the first one

---

