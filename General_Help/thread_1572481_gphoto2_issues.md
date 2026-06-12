---
title: "gphoto2 issues"
date: 2010-09-11
forum: General Help
---

### Post by Quan-Time on 2010-09-11
ubuntu x64, Nikon D90

the %n switch seems to no longer work when issuing the command:
```

gphoto2 --capture-image-and-download -I 20 --filename image%05n.jpg

```
2 weeks ago it worked flawlessly, same camera (nikon D90) but now it WONT label the filenames correctly.  It wants to keeps overwriting the same file and wont change the filename.

I tried to use --capture-image and it was saving the files onto the camera fine, but trying to get any files off after with -p gave no result.  Trying to list all files with -L said the camera was empty ? even tho it clearly stated it was saving each file.

Either way, 1044 pictures and a chance at a time lapse is now ruined. Still, thought i would pass some information along to try and get this sorted for next time.

---

