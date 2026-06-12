---
title: "Moving folders..."
date: 2011-09-07
forum: General Help
---

### Post by blueb73 on 2011-09-07
This should be easy, but maybe not.

I want to move about 10 folders that are in a sub-folder (x).

In x there are also some files that I do not want to copy.

Looks like this 

ls x

folder 1
folder 2
...
folder 10
file 1
file 2
file 3

now, using nautilus, i could do this in 2 seconds, but i am trying to learn the command line, and I cant find the answer.

I have googled and used my books, but all i see is how to move the folders and files, or one at a time, but not how to exclude the files!

argh!

any ideas?

Thanks!

---

### Post by papibe on 2011-09-07
You need a little script to do that:
```

for f in *; do
    if [ -d "$f" ]; then
        mv -- "$f" /path/to/destination
    fi
done

```
Basically: for every entry in the directory check if it is a directory. If it is, move it to another location.

Hope it helps,
Regards.

---

### Post by YesWeCan on 2011-09-07
find x/* -prune -type d -exec mv '{}' new_directory \;

The new_directory must already exist

---

### Post by sujoy on 2011-09-07
```
mv x/*(/) /where/you/want/to/copy/

```

Note: This works in zsh alright. Not tested for other shells.

---

