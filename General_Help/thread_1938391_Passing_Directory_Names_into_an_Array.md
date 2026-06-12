---
title: "Passing Directory Names into an Array"
date: 2012-03-09
forum: General Help
---

### Post by hateborne on 2012-03-09
Is there a simple way to pass directory names into an array, such as in a shell script?

The reason being is the need to delete a single file in each of a network user profile. Going through each user's folder manually isn't too troublesome if I did not have to do it ~130 times.

Any help would be greatly appreciated!

-Hate

---

### Post by hateborne on 2012-03-09
Found it:
```
array=( $( ls -1p | grep / | sed 's/^\(.*\)/\1/') )
```

Next, does anyone know how to log a "permission denied" error when using "rm -v /path/to/file.extension"? Currently a successful removal goes to MyLog.log and all is right with the world. However if a 'permission denied' is returned, then it ignores the ">> MyLog.log" and prints into terminal instead. 

Any suggestions?

-Hate

---

### Post by Dave_L on 2012-03-09
Have you tried ">>MyLog.log 2>&1" ? That redirects stderr (2) to the same place as stdout (1).

---

### Post by hateborne on 2012-03-09
You Sir, are amazing.

Thank You!

-Hate


(Anywhere I can set this to solved?)

---

### Post by Vaphell on 2012-03-09
parsing output of ls command will blow up in your face sooner or later

you should use builtin globs, something along the lines of
```
for dir in /home/*; do echo rm "$dir"/single.file; done
```


and [solved] is in 'thread tools' menu

---

