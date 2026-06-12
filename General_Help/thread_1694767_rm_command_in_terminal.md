---
title: "rm command in terminal"
date: 2011-02-24
forum: General Help
---

### Post by Zalib on 2011-02-24
Ok so this is a weird problem:

So I want to remove a file and I have to use the rm command however the filename has a space and a ' in the name which produces three ' which is bad I'm guessing. So what is a good solution to this? Do I just use " instead?

---

### Post by wiggly81 on 2011-02-24
```
sudo rm "file name here"
```
that should work for you

---

### Post by Telengard C64 on 2011-02-24
You can try using backslash escapes (\) to protect metacharacters from being eaten by the shell. For example if your file name contains the backtick character (`) you could do it like this.

```
rm -iv file\`name
```

If the file name contains a single quote mark (') you can surround it with double quotes (") like so.

```
rm -iv "file'name"
```

Single quote marks can also protect double quote marks.

```
rm -iv 'file"name'
```

[http://www.gnu.org/software/bash/manual/html_node/Quoting.html#Quoting]("http://www.gnu.org/software/bash/manual/html_node/Quoting.html#Quoting")

---

### Post by seawolf167 on 2011-02-24
And don't forget about tab completion so you don't have to type all the escape &/or special characters - start typing and hit tab once to attempt completion, twice (if what you have typed so far isn't unique) for a list of possible completions

---

