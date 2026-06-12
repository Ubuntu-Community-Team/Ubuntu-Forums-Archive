---
title: "Can't open a .zip archive"
date: 2009-09-26
forum: General Help
---

### Post by razor180 on 2009-09-26
I've installed 7zip (and I double checked to make sure) and every time I try to go into a .zip archive or extract one, I get the same error message saying

"7-Zip  4.58 beta  Copyright (c) 1999-2008 Igor Pavlov  2008-05-05
p7zip Version 4.58 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,1 CPU)

Error: /home/razor/Desktop/blender2kt_u9linux090913.zip is not supported archive

Errors: 1"

Now I'm doing this so I can install a blender exporter for kerkythea (a free renderer, a good one too, the only archive I found of it was a tar.gz file, but I found a way around actually having to use the terminal, I just extracted it then stuck it in my home folder and made a graphical link to the execution file). I need it so I can put my blender models in it and render in it without having to redo all of my materials

---

### Post by credobyte on 2009-09-26
```
sudo apt-get install p7zip unrar rar

```

---

### Post by razor180 on 2009-09-26
> **credobyte said:**
> ```
sudo apt-get install p7zip unrar rar

```
didn't think that would work, but I tried it, and it didn't work

thanks though, but I already have 7zip completely installed (using add/remove programs)

does it help to know that I'm using 9.04 ubuntu studio?

---

### Post by j7%&lt;RmUg on 2009-09-26
```

sudo apt-get install zip

```

if you cant open it through the shell try through the GUI.

---

### Post by razor180 on 2009-09-26
well that didn't work

I'm trying to extract it through the gui (right click extract here, or right click open) and nothing

I'll see if I can figure out how through the terminal

---

