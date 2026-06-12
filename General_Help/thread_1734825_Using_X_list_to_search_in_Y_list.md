---
title: "Using X list to search in Y list"
date: 2011-04-20
forum: General Help
---

### Post by Rabblerouser on 2011-04-20
I have two text files each with a list of a random string within them.  I would like to see which strings X has that Y does not.  All within the terminal.

I thought I could use grep in this case, but it doesn't seem to work.

Help would be awesome! :)

---

### Post by ttshivers on 2011-04-20
Are the strings separated by anything?  Any delimiter?

---

### Post by Rabblerouser on 2011-04-20
There is one string per line.

---

### Post by ttshivers on 2011-04-20
Do the strings have spaces?

---

### Post by Rabblerouser on 2011-04-20
They don't.  To be a bit more precise, the strings are filenames with extensions, each on their own line.

---

### Post by ttshivers on 2011-04-20
You can make a bash script for this:
```
cat dir1.txt | while read line
do
grep "$line" dir2.txt >> lines_that_dir2_has_that_dir1_doesn't.txt
done
```

---

### Post by ttshivers on 2011-04-20
You can also use the diff command([http://linux.about.com/library/cmd/blcmdl1_diff.htm]("http://linux.about.com/library/cmd/blcmdl1_diff.htm")) to do this.

You could do something like this
```
diff a1.txt b1.txt
```

---

