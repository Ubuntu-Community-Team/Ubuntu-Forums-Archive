---
title: "How to find file that is breaking copy operation"
date: 2006-06-14
forum: General Help
---

### Post by Varth on 2006-06-14
Hello.

I've been trying to copy some files off of a computer and on to another computer on the network, for backup purposes. However, the copy operation stops partway through. What's the fastest and easiest way to determine which file it's stopping at?

Thanks in advance.

---

### Post by mlind on 2006-06-14
Try using 'rsync' instead. Here's a example how to use rsync to copy
files over network [http://builder.com.com/5100-6372_14-6050168.html](http://builder.com.com/5100-6372_14-6050168.html)

adding -v (verbose) and --progress switches should help to determine any problems.

---

### Post by Varth on 2006-06-14
I'd rather use Nautilus if possible, because I'm already familiar with it. Does Nautilus have some sort of debug mode? That would probably show me which file is breaking it, right? I can't find a debug mode listed in the man page, though...

[EDIT]

From what I understand, rsync is for syncing files over a network. I'm not interested in syncing. I just need to copy the files over to another place temporarily, because the computer I'm getting them off of needs a format and reinstall.

---

### Post by mlind on 2006-06-14
[QUOTE=Varth]I'd rather use Nautilus if possible, because I'm already familiar with it. Does Nautilus have some sort of debug mode? That would probably show me which file is breaking it, right? I can't find a debug mode listed in the man page, though...
[/QUOTE]

I don't think so, nautilus is pretty bad for file larger scale file operations..

[QUOTE=Varth]
From what I understand, rsync is for syncing files over a network. I'm not interested in syncing. I just need to copy the files over to another place temporarily, because the computer I'm getting them off of needs a format and reinstall.[/QUOTE]

Did you check out rsync manual? It's replacement for rcp, which is used to copy
files between hosts on a network. Rsync can be used for syncing different sources,
but it's useful for copying too. Using rsync you don't have to start over if something
fails atleast. 

I'd move files over using scp or rsync.

---

### Post by mattkenn4545 on 2006-06-14
Why not do it one directory at a time or section of directories until you narrow it down (i know not what you were looking for but)

BTW I would be internested in this as well.

Just up cp -v (i think) and look at the output

---

### Post by Varth on 2006-06-14
[QUOTE=mattkenn4545]Why not do it one directory at a time or section of directories until you narrow it down[/quote]

Because there are 115 directories in the folder I'm trying to copy.

> Just up cp -v (i think) and look at the output

I'll give that a shot. But what would I use as a destination, seeing as how the folder I'm trying to copy to is on another computer on the network. Would I just use a smb:/// style filepath?

---

### Post by mlind on 2006-06-14
```

rsync -atvz /path/to/source yourhost.com:/target

```

using -t switch will only update differencies between files

---

