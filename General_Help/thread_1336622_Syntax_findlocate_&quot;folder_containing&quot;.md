---
title: "Syntax find/locate &quot;folder containing&quot;"
date: 2009-11-24
forum: General Help
---

### Post by riotculture on 2009-11-24
I am looking for a way to search for folders containing a certain file extension, eg. mp3's.

I need this in order to move these folders (albums) to another drive. As I have thousands og mp3's it is a bit exhaustive to to search for mp3 files, right click them for properties to find the album, then move the album.

So what i want is a command like:

Find/locate Music "folder containing" *.mp3 to get a list of all folders containing mp3 files.

---

### Post by lloyd_b on 2009-11-24
> **riotculture said:**
> I am looking for a way to search for folders containing a certain file extension, eg. mp3's.

I need this in order to move these folders (albums) to another drive. As I have thousands og mp3's it is a bit exhaustive to to search for mp3 files, right click them for properties to find the album, then move the album.

So what i want is a command like:

Find/locate Music "folder containing" *.mp3 to get a list of all folders containing mp3 files.

In a terminal window:```
find . -name "*.mp3" -exec dirname {} \;| sort -u
```will search from the current directory, finding all .mp3 files, then strip off the file name (leaving only the directory), and then sort the list of directories, eliminating any duplicates.

Is that more or less what you're looking for?

Lloyd B.

---

### Post by riotculture on 2009-11-25
Thank you

---

