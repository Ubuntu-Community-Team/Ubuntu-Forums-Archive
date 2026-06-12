---
title: "Files in home/ missing"
date: 2011-04-09
forum: General Help
---

### Post by victorius on 2011-04-09
I changed my default language and when I restarted, Ubuntu asked if I wanted to rename my folders (download etc).
I clicked yes and now I'm missing every file from my folders. Ex. documents, Music etc.

Now I have the folder names in my native languge but none of the files.

Is there any way I can get the files back or revert this?

---

### Post by techunit on 2011-04-09
You may want to reverse your search and see if your files got moved to another location in the previous language folders. It is likely to prevent errors and you aren't seeing them. Go to root and see if you can track down your files.

Good Luck

---

### Post by Bcrowes11 on 2011-04-09
Try ctrl + h. Sometimes folders get hidden.

---

### Post by techunit on 2011-04-09
> **Bcrowes11 said:**
> Try ctrl + h. Sometimes folders get hidden.
I doubt they got hidden but yeah its worth a try.

---

### Post by Bcrowes11 on 2011-04-09
you know it!

---

### Post by WorMzy on 2011-04-09
If you can remember one of the filenames, or part of one, then run the following command:
```
sudo updatedb && locate -i [COLOR="Red"]filename[/COLOR] | grep home
```

---

