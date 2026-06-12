---
title: "Moving files listed in text file?"
date: 2010-06-14
forum: General Help
---

### Post by Jay Colfer on 2010-06-14
I've got a text file listing 1823 files that need to be copied from their current locations, i.e.

> 
/media/blackhole/Audio/Music/whatever.mp3
/media/blackhole/Audio/Music/sowhat.mp3


To another folder, any idea how I should do this?

Thanks.

---

### Post by sisco311 on 2010-06-14
```
while read file; do
  cp -vb "$file" /path/to/dir
done < /path/to/file

```

---

### Post by Jay Colfer on 2010-06-14
> **sisco311 said:**
> ```
while read file; do
  cp -vb "$file" /path/to/dir
done < /path/to/file

```

I've got an idea how you mean for this to be used, but I'm kind of confused.

I'm thinking drop that code in a text file as move.sh, change /path/to/dir to the intended destination for all those files, and /path/to/file to the path to the text file full of files? i.e. foobar.txt?

so it'd look like 

```

#hope I got this right
while read file; do
  cp -vb "$file" /home/jay/test
done < /home/jay/foobar.txt
```

and then run it from the terminal, how far off base am I?

Thanks for the help!

---

### Post by sisco311 on 2010-06-14
> **Jay Colfer said:**
> I've got an idea how you mean for this to be used, but I'm kind of confused.

I'm thinking drop that code in a text file as move.sh, change /path/to/dir to the intended destination for all those files, and /path/to/file to the path to the text file full of files? i.e. foobar.txt?



Yep, you can create a scrip (move.sh) if you wish, but the code is very trivial an short you can type (copy/paste) it directly in the terminal. You can even write it in one line:
```
while read file; do cp -vb "$file" /home/jay/test; done < /home/jay/foobar.txt
```

Of course, if you plan to run it multiple times, then create a script:
```

#!/bin/bash
while read file; do
  cp -vb "$file" /home/jay/test
done < /home/jay/foobar.txt

```

Don't forget to make it executable:
```
chmod +x ./move.sh
```

---

### Post by Jay Colfer on 2010-06-14
Thanks, you're a life saver! I just moved all but a few of the files that had weird filenames that cp choked on, but that's easy enough to fix.

---

