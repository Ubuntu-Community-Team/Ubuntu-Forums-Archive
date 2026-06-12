---
title: "can't cd in terminal"
date: 2009-10-25
forum: General Help
---

### Post by coetzewc on 2009-10-25
Hi I have an external drive that gets mounted at startup at /media/New Volume

The New Volume is displayed om my Desktop, however I can not cd into that volume via terminal.

I am able to browse the volume through the gui and it is also possible to mout a volume name with no spaces like /media/darddrive for this device /dev/sdb1

Why can I not cd in terminal to a mounted volume with a space ie: (New Volume) the newley created volume name (mount point) Harddrive works perfectly in terminal.

Using 9.04 theis is an NTFS volume.

Please help.

---

### Post by nothingspecial on 2009-10-25
You need to escape the space with a \

```
cd /media/New[COLOR="Red"]\[/COLOR] Volume
```

---

### Post by dandnsmith on 2009-10-25
The space is taken as a terminator, so the "Volume" gets taken as a parameter or whatever. You need to escape the space with \ to get it taken as part of the name (IIRC)

---

### Post by Penguin Guy on 2009-10-25
In bash (the terminal) spaces mark a new command or parameter. Presumably you are using the command [COLOR="Red"]cd /media/New Volume[/COLOR], which will not work. To fix this you could either backslash-escape the space  or put quotes around the path:
```

[COLOR="Green"]cd /media/New**\** Volume[/COLOR]
or
[COLOR="Green"]cd **"**/media/New Volume**"**[/COLOR]

```

---

### Post by coetzewc on 2009-10-25
Perfect that works I'm not sure I understand the concept but I'll read up.

Thanks Guys!

---

### Post by coetzewc on 2009-10-25
Thanks guys,

Found a few other threads on BASH and spaces makes sence.

Thanks for your quick help all who responded.

Ubuntu people rocks

---

### Post by 3rdalbum on 2009-10-25
You can drag files from Nautilus into the terminal, and the full filepath (including properly-escaped characters) will be entered in there. You can use this with cd if you wish - saves a bit of typing!

---

### Post by coetzewc on 2009-10-25
Thanks yes, if you drag and drop it makes like Penguin Guy suggested 

 cd '/media/New Volume'

tnks

---

