---
title: "Unrar 4000+ files in directory with names that contain spaces"
date: 2011-12-02
forum: General Help
---

### Post by iamroddo on 2011-12-02
I have a stupid newby question. I have a bunch of rar files, more than 4000, all of which have file names that contain at least one space. unrar e ¨*.rar¨ ./ spits out an error. Can someone help me with the syntax that I would need to use to unrar these?

---

### Post by ajgreeny on 2011-12-02
Maybe you can remove the spaces and replace with an underscore before unrar does its work with ```
rename 's/\ /_/g' *
``` or to do all the files in a folder use ```
find ~/folder -name '*.rar' -exec rename -n 's/\ /_/g' "{}" +
```

I found these examples some time ago when I needed a similar job done quickly, so other than passing on the info, I am not clever enough to take any of the kudos if it works for you.  Just be thankful that I remembered doing this, and kept a note of the useful command.

---

### Post by btindie on 2011-12-02
You can just do it all in a for loop ->

```
for i in /tmp/file/*.rar; do unrar e "$i"; done
```cd to the directory you want to extract them to and update the above path to where the files are stored. You can see what it would do with ->

```
for i in /tmp/file/*.rar; do echo "unrar e \"$i\""; done
```

---

### Post by iamroddo on 2011-12-03
Thanks for the suggestions. They helped a lot!

---

