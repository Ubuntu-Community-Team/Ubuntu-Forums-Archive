---
title: "Creating an M3U file"
date: 2011-10-30
forum: General Help
---

### Post by Ron W on 2011-10-30
Hello.

I've downloaded some radio programmes that I would like to collate together as in a music album. I believe that I need to put the ones I want in an m3u file. Is there a programme that can easily create this file for me?

Thanks

Ron

---

### Post by mjuhasz on 2011-10-30
The .m3u files are basically just textfiles that list one MP3 or other media file on each line, normally with full path or URL to the file.
There must be gui applications to create m3u files or export their playlist as m3u, but if you're not afraid of commandline then cd into the directory with your mp3 files and run ```
find `pwd` -name '*.mp3' > playlist.m3u
```

---

