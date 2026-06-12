---
title: "Extracting problem"
date: 2009-10-14
forum: General Help
---

### Post by peanut_butter_kid on 2009-10-14
I don't if it's just the zip folder or a different error but I keep getting the message in the image. Anyone know what is going on??? :confused:

---

### Post by bodyharvester on 2009-10-14
does the zip contain only one file? open it with archive manager and manually move the files you want out (drag & drop, if im not mistaken). the file that wont is the corrupted one which is giving you this error

---

### Post by peanut_butter_kid on 2009-10-14
> **bodyharvester said:**
> does the zip contain only one file? open it with archive manager and manually move the files you want out (drag & drop, if im not mistaken). the file that wont is the corrupted one which is giving you this error

No it contains many images as it is part of a whole volume of a manga. If I lose one image it could throw me off on what happen. Are you sure it's just a corrupt file? I redownloaded it and still got the same error.

---

### Post by Giblet5 on 2009-10-14
If you didn't create the zip file then you can't possibly know what is in it.

Test the archive: ```
unzip -t myfile.zip
```

That will list the files in it too.

If all seems cool so far, you could extract the files via: ```
mkdir manga
cd manga
unzip ../myfile.zip
```

I'll wager that won't work though, because Ark would have been able to do the same thing.

---

