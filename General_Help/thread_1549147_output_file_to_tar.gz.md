---
title: "output file to tar.gz"
date: 2010-08-09
forum: General Help
---

### Post by jrriss on 2010-08-09
```
ffmpeg -i 'movie.flv' movie%d.png
```


Is there a way I can output "movie%d.png" to a tar.gz archive?

---

### Post by rubylaser on 2010-08-09
Sure,
```
ffmpeg -i 'movie.flv' movie%d.png && tar czf movie.tar.gz *.png
```

Should do it.

---

### Post by elliotn on 2010-08-09
Right click on the png and choose create an archieve that will make it to tar.gz

---

### Post by jrriss on 2010-08-09
I meant output directly to tar.gz

---

### Post by WorMzy on 2010-08-09
No. tar.gz is not an image format.

---

### Post by elliotn on 2010-08-09
.tar.gz is an archieve format like .zip or .rar

---

