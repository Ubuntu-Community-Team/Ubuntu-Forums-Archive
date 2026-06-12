---
title: "Move contents of a directory up a level (command line)"
date: 2009-09-11
forum: General Help
---

### Post by il1019 on 2009-09-11
I'm trying to figure out how to do this, and it's something that I run across fairly often, but can't figure out how to do it except in nautilus.

I have a folder (/mnt/music/My MP3s) and I want to move the contents of My MP3s up a level, so everything currently in My MP3s resides in music. I tried

mv -t /mnt/music /mnt/music/My\ MP3s

but that tries to move the directory as well as it's contents. I get an error saying that folder already exists. I'm really at a loss here. How should I format this command?

Oh and I don't have enough room to copy the files and then delete the orginal set, so that isn't an option.

---

### Post by ecmatter on 2009-09-11
```

mv /mnt/music/My\ MP3s/* /mnt/music

```

---

