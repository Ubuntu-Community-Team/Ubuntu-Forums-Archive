---
title: "want to replace file with new name?"
date: 2010-03-19
forum: General Help
---

### Post by tigs6969 on 2010-03-19
ive been trying to move 170gb of music from my computer to my new archos  500gb
windows isnt an option as ubuntu is my only os from now on
anyway my problem is some songs  are same names and theres so many of them itd be a complete bitch to  change the names
so when i go to add them they say replace or skip...  is there anyway i can get the option like on windows where you add but  it adds a (2) to it? or am i gonna go the hard way?

---

### Post by mastermindg on 2010-03-19
Why not just replace the files? If they are the same name, why wouldn't you just replace them?

---

### Post by tigs6969 on 2010-03-19
over 67 000 songs  with over 1900 bands i enjoy alot of music and as is usual some songs have same names but are different songs by different bands.
does this mean i cant do what im asking??

---

### Post by kamaji792 on 2010-03-19
Just checked **man cp** and there is a **--babckup=numbered** option that would appear to do what you want.  Though I think it renames the target file, not the file you are copying.

```
man cp
```

Search for CONTROL by typing "/CONTROL" and pressing the return key.
**n** and **Shift+n** to search forward and backward.

[EDIT]
Actually what this does is add ~1~, ~2~ etc. to the end of the original files.  So text.txt becomes text.txt~1~ and I guess that is not going to help you unless you post process them.

atb

---

### Post by ajlee on 2010-03-19
I haven't tested this, but it looks like it would do what you need.  I would suggest you test in different directory with only a few files in it first.

[http://6v8.gamboni.org/Mass-renaming-with-linux-shell.html](http://6v8.gamboni.org/Mass-renaming-with-linux-shell.html)

Hope it helps!

---

### Post by n0dix on 2010-03-19
Or delete repeated files

---

