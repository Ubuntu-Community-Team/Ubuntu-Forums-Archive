---
title: "copy folder location and save in text file"
date: 2010-05-17
forum: General Help
---

### Post by CatchItBaby on 2010-05-17
I want to copy location of every .avi , .jpg file present in a folder or in subfolder present in a direcotry and save in a textfile how to do

ex : /home/username/Desktop/bookofeli/video/book.avi

it should give full locaiton of path how to do

thanks

---

### Post by sisco311 on 2010-05-17
try:
```
find /full/path/to/dir -iname *.avi -o -iname *.jpg 1> pth/to/file
```

---

### Post by CatchItBaby on 2010-05-22
Thanks a lot..

It work's

---

