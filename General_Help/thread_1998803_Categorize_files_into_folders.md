---
title: "Categorize files into folders"
date: 2012-06-07
forum: General Help
---

### Post by balasankarc on 2012-06-07
Hi all,

I am using Ubuntu 12.04 with GNOME Shell 3.4..Is there a way to automatically move the files of a folder to sub-folders according to their file type...
For example, I've a folder called 'Downloads' with all the files i downloaded... i want to move all the document type files (those with extensions .doc, .odt, .pdf etc) to a sub-folder  called "Documents", all music files(.mp3,.wma etc) to a sub-folder called "Music", all video files(.avi, .flv, .mpg, .mp4 etc) to a sub-folder called "Videos" etc... Is there a way to do this... Either GUI or via terminal.

Thanks,
Balasankar C

---

### Post by nothingspecial on 2012-06-07
```
mv *.{doc,odt,pdf} Documents
```

```
mv *.{avi,flv,mpg,mp4} Videos
```

etc

from inside the directory



You have to create the folders first.

---

### Post by Erik1984 on 2012-06-07
For KDE there is a plasma widget called magic folder (I believe based on a similar function on OSX) where you can drag files in that are then moved to the desired places based on extension. Don't know if something similar exists for Gnome.

I guess somebody must have made a bash script for this, must not be that hard:
- loop over all files in ~/Downloads and for each file:
- Determine MIME type (don't know exact command but you can grab this for every file)
- mv file /some/new/location/file based on MIME type

---

### Post by balasankarc on 2012-06-07
> **nothingspecial said:**
> ```
mv *.{doc,odt,pdf} Documents
```

```
mv *.{avi,flv,mpg,mp4} Videos
```

etc

from inside the directory



You have to create the folders first.

Thanks man... That did it...

---

