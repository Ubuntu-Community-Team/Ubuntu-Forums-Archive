---
title: "command line tool to split a image into 4 sections"
date: 2012-01-01
forum: General Help
---

### Post by coffeecake on 2012-01-01
hi all. I have quite large images of resolution 1600 by 1200. I wanna split them into 4 sections. I cannot do manually as i need to do it on a large collection of images. Does anyone know of a command line tool that could do this to me ?

---

### Post by sisco311 on 2012-01-01
You can use the convert command from the imagemagick package:
```
convert "file name.png" -crop 50%x50% +repage "file name %d.png"
```

---

### Post by coffeecake on 2012-01-01
> **sisco311 said:**
> You can use the convert command from the imagemagick package:
```
convert "file name.png" -crop 50%x50% +repage "file name %d.png"
```


How can i get the other 3 parts ?

---

### Post by sisco311 on 2012-01-01
The command will create 4 new files: "file name 0.png", "file name 1.png" and so on...

---

