---
title: "Bash script to rename files?"
date: 2011-09-20
forum: General Help
---

### Post by Quikj on 2011-09-20
Hello everyone, thanks for taking the time to read my post.

I'm having trouble renaming multiple files within a given directory. I have a bunch of .mp3 files that were mistakenly renamed so that there is now a '2' in front of the .mp3 extension. 

For example: "10 Lip Gloss and Black 2.mp3"

I'd like it to read: "10 Lip Gloss and Black.mp3"

I just realized that i also would like to get rid of the empty string between the '2' and the song title. 

I've reached the wall of my bash skill level as the closest that I've gotten is this:

```
rename -n "s/\.mp3$//" *.mp3
```

However, this command only removes the .mp3 tag.

Any and all suggestions would be greatly appreciated.

---

### Post by sisco311 on 2011-09-20
The syntax is very simple s/foo/bar/ = replace foo with bar.

You want to replace ' 2.mp3' with '.mp3' (without the quotes), right?

```
rename -n 's/ 2\.mp3$/.mp3/' *.mp3
```

---

### Post by seawolf167 on 2011-09-20
What about this:

```
for file in *2.mp3
do mv "$file" "${file%2.mp3}.mp3"
done
```

---

### Post by scarleo on 2011-09-20
Theres a benefit with using rename, the -n option lets you test first to make sure you get desired result before actually doing anything

---

### Post by sisco311 on 2011-09-20
> **scarleo said:**
> Theres a benefit with using rename, the -n option lets you test first to make sure you get desired result before actually doing anything

In bash, we could use the echo command to test our script:
```
#!/bin/bash

shopt -s nullglob
cd /path/to/files || exit 1

for file in *\ 2.mp3
do
    **echo** mv -b -- "$file" "${file% 2.mp3}.mp3"
done

```

---

### Post by Quikj on 2011-09-20
> **sisco311 said:**
> The syntax is very simple s/foo/bar/ = replace foo with bar.

You want to replace ' 2.mp3' with '.mp3' (without the quotes), right?

```
rename -n 's/ 2\.mp3$/.mp3/' *.mp3
```

Thank You!!! This worked beautifully. Now I feel a bit silly, but i'll apply the proper syntax next time around. 

Thank you everyone for your help.

---

