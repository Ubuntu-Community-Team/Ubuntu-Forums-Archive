---
title: "WinFF"
date: 2011-08-28
forum: General Help
---

### Post by shashanksingh on 2011-08-28
While I was trying to convert a .mkv to  a .avi, I got the following error on the terminal:

```
Unknown encoder 'libmp3lame'
```

I did search for that package, but there is no package called libmp3lame.

I installed libmp3lame0 , which was the only package I found, but it doesn't resolve the error.

---

### Post by beew on 2011-08-28
I think you need to replace the packages libavcodec-52 with libavcodec-extra52, and libavformat-52 with libavformat-extra52 To do this you need to add the medibuntu ppa and then install the packages w32codecs and non free codecs and it will pull in the extra52 packages as dependencies.

[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1656-how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1656-how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui)

---

### Post by shashanksingh on 2011-08-29
Thank You. Worked :)

---

