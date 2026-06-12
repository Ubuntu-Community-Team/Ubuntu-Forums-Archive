---
title: "Bash for playing directories full of music"
date: 2012-08-20
forum: General Help
---

### Post by supradave on 2012-08-20
I've been trying and trying to figure out this problem, I have music in subdirectories due to a large amount or how I have it sorted or anything. 

If I process the file names and remove spaces and special characters, everything works.  I don't necessarily want to do this. 

I go the the directory I want and:

```
find . -type f -iname "*flac" | sort | while read FILEN; do echo "$FILEN" | mplayer; done
```

This command start playing the first piece but then goes into strange behavior, skipping and jumping in the file.

I've tried:

```
mplayer `find . -type f -iname "*mp3" | sort`
```

This one doesn't work at all

```
find . -type f -iname "*flac" -exec mplayer
```

works fine except the playlist isn't sorted based on filename.

Any ideas?

---

### Post by TheFu on 2012-08-20
Interesting. I've used similar 'find' commands and didn't have any issues with mplayer, but I don't usually do anything once they start playback.  Those appear fine to me, but I've never sorted the output.

Have you tried to put the intermediate output into the file and using that to feed mplayer with the ```
mplayer -playlist 
```option?

Or turning it around```

find . -type f -iname "*mp3" | sort | mplayer -
```

---

