---
title: "How to find files with no file extension?"
date: 2009-12-16
forum: General Help
---

### Post by Rytron on 2009-12-16
Hi.
How do I find files with no file extension? 
For example, how do I find files such as [COLOR="DarkOrange"]**shop-list**[/COLOR] as I want to rename it to **[COLOR="DarkOrange"]shop-list[/COLOR][COLOR="DarkGreen"].txt[/COLOR]**
I like to have all files with their appropriate file extension.

---

### Post by KeLa on 2009-12-16
have you tried this:
```
mv ./shop-list ./shop-list.txt
```

---

### Post by Rytron on 2009-12-16
> **KeLa said:**
> have you tried this:
```
mv ./shop-list ./shop-list.txt
```

Hi KeLa. 
You misunderstood me, I used the file [COLOR="DarkOrange"]**shop-list**[/COLOR] as an example. I know how to rename the files, I want a way to find them all. I have many sub folders and don't want to spend ages manually searching through them to find the no extension files.

---

### Post by tjoff on 2009-12-16
To list it for the current directory, maybe this is what you want:

find . -maxdepth 1 -type f ! -name "*.*"

To do it recursively, just remove "-maxdepth 1"

---

### Post by Rytron on 2009-12-16
> **tjoff said:**
> To list it for the current directory, maybe this is what you want:

find . -maxdepth 1 -type f ! -name "*.*"

To do it recursively, just remove "-maxdepth 1"

Thank you tjoff. Works perfectly.
:popcorn:

---

### Post by 3rdalbum on 2009-12-16
> **KeLa said:**
> have you tried this:
```
mv ./shop-list ./shop-list.txt
```

Should be:

```
mv shop-list shop-list.txt
```

The ./ is redundant.

You might be able to use some sort of mass file renaming program. There are a few around in the repositories.

---

### Post by Rytron on 2009-12-16
GPRename is my favourite.

---

### Post by KeLa on 2009-12-16
You can try this:
```
find ~/test/ -type f ! -name "*.*" -exec rename -v 's/$/\.txt/' {} \;
```

It will search all files that have no extension from test directory under your home directory and add .txt extension to all of those recursively.
This worked on my tests very well.

---

### Post by Rytron on 2009-12-16
Excellent code, KeLa. :popcorn:

NOTE: **Don't** use this in home folder as it will rename hidden files and this will cause problems. Instead use in sub folders **ONLY**!

---

