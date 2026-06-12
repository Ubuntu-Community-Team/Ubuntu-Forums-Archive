---
title: "How can I play random videos in a directory from the terminal..."
date: 2012-03-09
forum: General Help
---

### Post by Rytron on 2012-03-09
Hi.

How can I play random (shuffle) videos in a directory from the terminal? I'd also like it to auto make a playlist of 10 files.

Thanks.

---

### Post by nothingspecial on 2012-03-09
Assuming your videos are in your Videos folder

```
mplayer -quiet -shuffle -playlist <(find ~/Videos -type f)
```

You can skip past any you don't want to watch with >

Note: That will play any media file in your Videos folder.

---

### Post by dandnsmith on 2012-03-09
Didn't see there was a reply until I attempted one.

---

### Post by Rytron on 2012-03-09
> **nothingspecial said:**
> ```
mplayer -quiet -shuffle -playlist <(find ~/Videos -type f)
```

How can I use it to play videos in the current directory? Can it also look into sub directories?

---

### Post by dandnsmith on 2012-03-09
```
mplayer -quiet -shuffle -playlist <(find . -type f)
```

That should get the current directory, and is easy to extend to recursive search if it isn't going to do it anyway - I suggest looking at the man page for *find*

---

### Post by Rytron on 2012-03-09
> **dandnsmith said:**
> ```
mplayer -quiet -shuffle -playlist <(find . -type f)
```

That should get the current directory, and is easy to extend to recursive search if it isn't going to do it anyway - I suggest looking at the man page for *find*

I ran the above command inside a folder with 3 movie files (has 3 parts and has no sub folders). Got this error:

```
player -quiet -shuffle -playlist <(find . -type f)

[COLOR="DarkRed"]MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/fd/./1201 PM (Part 23).mp4.
File not found: '/dev/fd/./1201 PM (Part 23).mp4'
Failed to open /dev/fd/./1201 PM (Part 23).mp4.[/COLOR]
```

---

### Post by dandnsmith on 2012-03-10
You haven't provided a list of the files, but I'd hazard a guess that the problem is the space(s) within the filename. You could quickly check this manually. If it is so, then you need to quote the filename(s) before passing them to mplayer - I cannot quickly see how this should be done, but I'm sure someone else can provide an answer (which may call for a for-loop to be built in to quote each filename before passing on).

---

### Post by nothingspecial on 2012-03-10
To play all the files in the current directory randomly just do

```
mplayer -quiet -shuffle *
```

If there are subdirectories you can use

```
mplayer -quiet -shuffle {*,*/*}
``` to go one level deep.

---

### Post by Rytron on 2012-03-10
> **dandnsmith said:**
> You haven't provided a list of the files, but I'd hazard a guess that the problem is the space(s) within the filename. You could quickly check this manually. If it is so, then you need to quote the filename(s) before passing them to mplayer - I cannot quickly see how this should be done, but I'm sure someone else can provide an answer (which may call for a for-loop to be built in to quote each filename before passing on).

There are too many files to list.

---

### Post by Rytron on 2012-03-10
> **nothingspecial said:**
> To play all the files in the current directory randomly just do

```
mplayer -quiet -shuffle *
```

If there are subdirectories you can use

```
mplayer -quiet -shuffle {*,*/*}
``` to go one level deep.

Excellent stuff! ;)

---

