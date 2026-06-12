---
title: "rmdir directories that only contain subdirs?"
date: 2011-11-07
forum: General Help
---

### Post by Gias Kay on 2011-11-07
Suppose I have a dir tree like this:

DIR
  &#9492;--SUBDIR1
[INDENT]  &#9492;----SUBDIR2[/INDENT]
[INDENT][INDENT]  &#9492;----SUBDIR3[/INDENT][/INDENT]

I am looking for a command that when I input:

```
$ *[unknown command]* DIR
```

The whole dir tree can be deleted *if there is no file but dirs inside the whole tree*; however if there is a file under SUBDIR1, the command only deletes SUBDIR2 and below.

Is there anything like this? Thanks!

---

### Post by papibe on 2011-11-07
You would need to write a bash scripts to accomplish that.

Here are a few pointers:

To find out if there's files under a tree structure you can use the command 'find':
```
find DIR/ -type f
```
You can even count how many if you 'pipe' the result to a command that count lines:
```
find DIR/ -type f | wc -l
```
You can assign the result of that command to a variable like this:
```
nfiles=$(find DIR/ -type f | wc -l)
```
Then you can test if the number of files is zero:
```
if [ $nfiles = 0 ]
then
    ...
else
    ....
fi

```
I hope this points you in the right direction.
Regards.

---

