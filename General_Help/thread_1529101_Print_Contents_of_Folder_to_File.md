---
title: "Print Contents of Folder to File"
date: 2010-07-11
forum: General Help
---

### Post by jaqian on 2010-07-11
I've a lot of music on my pc and unfortunately I didn't know what I was doing so a lot is low bitrate and not tagged.

I want to know is it possible to create a list of all files (mp3, wma & ogg) and display name and bitrate and print to a text file?

Using Linux Mint Isadora.

---

### Post by geirha on 2010-07-11
Seems the file command manages to detect the bitrate of vorbis and mp3 at least (don't have any wma to test with), so this might be all you need: 
```
file *.mp3 *.wma *.ogg > filelist.txt
```

If you want it done recursively, you can use [find](http://mywiki.wooledge.org/UsingFind)
```
find ./ -type f \( -iname "*.mp3" -o -iname "*.wma" -o -iname "*.ogg" \) -exec file {} + > filelist.txt
```

---

