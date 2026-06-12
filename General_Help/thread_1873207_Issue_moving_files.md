---
title: "Issue moving files"
date: 2011-11-01
forum: General Help
---

### Post by CerialPhreak on 2011-11-01
So I've got a directory with a large amount of sub directories. I want to move the files from the sub directories into the parent directory. Is there a way to do this from the console (all at once preferably)?

---

### Post by 3rdalbum on 2011-11-01
Not having lots of subdirectories and files that I can move on my computer, I'd imagine something like this would work:

```
mv /home/cerialPhreak/directory/*/ /home/cerialPhreak/directory/
```

---

### Post by papibe on 2011-11-01
Here are several examples:

From above directory:
```
$ mv directory/subdirectory1/* directory
```
From directory:
```
$ cd directory
$ mv subdirectory1/*  .
```
From subdirectory1:
```
$ cd subdirectory1
$ mv *  ..
```
Hope it helps,
Regards.

---

### Post by Telengard C64 on 2011-11-01
Start in the parent directory and use the **find** command to move all the files. Example:

```
$ cd /path/to/parent-directory
$ find -mindepth 2 -type f -exec mv -it . {} \;
```

Don't just blindly type this in! Make sure it is what you want first.

Here's a sample run:

```
tmp$ mkdir -pv parent-dir/subdir{1..3}
mkdir: created directory `parent-dir'
mkdir: created directory `parent-dir/subdir1'
mkdir: created directory `parent-dir/subdir2'
mkdir: created directory `parent-dir/subdir3'
tmp$ for i in {1..3} ; do touch parent-dir/subdir$i/file$i ; done
tmp$ cd parent-dir
parent-dir$ ls -R
.:
subdir1  subdir2  subdir3

./subdir1:
file1

./subdir2:
file2

./subdir3:
file3
parent-dir$ find -mindepth 2 -type f -exec mv -ivt . {} \;
`./subdir2/file2' -> `./file2'
`./subdir3/file3' -> `./file3'
`./subdir1/file1' -> `./file1'
parent-dir$ ls
file1  file2  file3  subdir1  subdir2  subdir3
parent-dir$
```

---

### Post by CerialPhreak on 2011-11-01
Thanks telengard! That looks like exactly what i need!

---

### Post by papibe on 2011-11-01
Replace subdiirectory1 with a '*' in the example above:
```
$ mv directory/*/* directory
```
or
```
$ cd directory
$ mv */* .
```
**[COLOR="Red"]Note[/COLOR]** that moving files from different directories into one, creates the possibility of losing files. You may overwrite (and lost) files with the same name.

You could be safe and use the interactive option (-i) to tell you if something is being overwritten. If you answer 'no', the move won't be done, and no file will be lost.
```
$ cd directory
$ mv -i */* .
```
However you will end up with some files in the parents directory and some on the subdirectories. Then it would be necessary to design another method to move up the remaining files.

If the possibility of losing files is a big concern, then I let us know so we can suggest you other options.

Hope it helps,
Regards.

---

### Post by Telengard C64 on 2011-11-01
> **CerialPhreak said:**
> Thanks telengard! That looks like exactly what i need!

You are welcome. If that works for you, then please consider [marking this thread solved](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads).

---

