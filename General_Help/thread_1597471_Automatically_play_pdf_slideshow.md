---
title: "Automatically play pdf slideshow"
date: 2010-10-15
forum: General Help
---

### Post by hus- on 2010-10-15
Hey, first post! I'm looking for a script to automatically open and play a PDF slideshow. The slideshow is saved in PDF format using powerpoint. Are there any good programs out there that I can use to play a pdf slideshow. 

We tried to implement this while in its original PPT format but there are just too many issues. Here is the original script I wrote to open the PPT file using pptviewer

```
#!/bin/bash
echo "OK, starting now..."
export DISPLAY=:0.0
killall PPTVIEW.EXE

FILENAME="/home/mistequay/powerpoint/admin.ppt"
"pptview" "$FILENAME" &
```

And here is the code that imports the file from a central server before opening the file. 

```
#!/bin/sh
rsync -e 'ssh' -avzp root@mgl***:/var/www/html/***.*****.com/powerpoint /home/m****
```

Then using cron, the scripts are run at the appropriate times. Basically I am just looking for a program that will play a PDF as a slideshow. I will use OpenOffice if I can but I would rather not because we have had problems with it. Plus im not sure how to run it from terminal. 

Thanks!

---

### Post by hus- on 2010-10-15
bump

---

### Post by hus- on 2010-10-18
bump

---

### Post by hus- on 2010-10-18
bump

---

