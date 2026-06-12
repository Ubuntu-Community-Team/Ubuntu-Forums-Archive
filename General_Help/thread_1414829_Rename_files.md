---
title: "Rename files"
date: 2010-02-24
forum: General Help
---

### Post by CatchItBaby on 2010-02-24
I want to add suffix or prefix in all files (.txt , .avi . , .exe)from a folder 

how to do that

---

### Post by guren on 2010-02-24
mv dir_name/filename dir_name/filename.txt

or

cd dir_name
mv filename filename.txt

---

### Post by darolu on 2010-02-24
You can do it with **mmv**, first install it with:
```
$ sudo apt-get install mmv
```
Then say you have 200 files in a directory, all without extension (suffix) and you want them all to have .txt then you would do:
```
$ mmv "*" "#1.txt"
```
And that's it. mmv is quite powerful, read the man to learn all you can do, you can even use [regular expressions]("http://en.wikipedia.org/wiki/Regular_expression").

IIRC, there is a Nautilus plug in that can do this too, but I don't remember its name.

---

### Post by CatchItBaby on 2010-02-24
It give error

Couldn't connect to server

---

### Post by cjhabs on 2010-02-24
You can do this easily from the command line in bash.
cd to the folder then, to rename all files to add a .txt extension:
Note that the > is a continuation prompt from the shell:
for file in *
> do
> mv $file $file.txt
> done

That is it.

---

### Post by wojox on 2010-02-24
+1 for mmv. Try:

```
sudo apt-get update && sudo apt-get install mmv
```

---

### Post by CatchItBaby on 2010-02-24
It give error coudn't connect (didn't increase from 0%)

[IMG]http://i46.tinypic.com/jrxv74.jpg[/IMG]

---

### Post by cong06 on 2010-02-24
Do you have internet? That's kind of important.

(I've been using gprename, but mmv sounds sweeter, thanks!)

---

### Post by sulimir on 2010-02-24
> **cjhabs said:**
> You can do this easily from the command line in bash.
cd to the folder then, to rename all files to add a .txt extension:
Note that the > is a continuation prompt from the shell:
for file in *
> do
> mv $file $file.txt
> done

That is it.

I would recommend following the advice of cjhabs.  To do this all on one line try:

```
for file in *; do mv $file ${file}.txt; done
```

To remove that extension you could then do this

```
for file in *.txt; do mv $file ${file/\.txt/}; done
```

---

### Post by kaibob on 2010-02-24
The rename command is another way to do what you want. To add a prefix to all files in the current directory:

```
rename -n 's/^/new/' *
```

To add a suffix:

```
rename -n 's/$/new/' *
```

Change "new" in the above command lines to whatever characters you want to add to the file name. The -n option tells rename to do a dry-run and report proposed changes. Substitutue -v for -n to actually rename the files. Just as a word of caution, the rename command also renames directories, so be sure to start with the -n option.

---

### Post by CatchItBaby on 2010-02-26
I hv many files are in folder's and contain sub folder's and sub folder's

how to do in that case ?

---

### Post by cjhabs on 2010-02-26
You would use the find command to find all the files, such as:
find . -type f -exec mv {} {}.txt \;
Please test this and understand it before running it in a real folder!

---

### Post by CatchItBaby on 2010-02-28
How i can use this command for adding suffix and preffix

> find . -type f -exec mv {} {}.txt \;

i hv some text file i want to rename those text file with my name like

1.txt
2.txt
3.txt

After running command's it will look like this

Catchitbaby1.txt
Catchitbaby2.txt
Catchitbaby3.txt

---

### Post by cjhabs on 2010-02-28
> **CatchItBaby said:**
> How i can use this command for adding suffix and preffix



i hv some text file i want to rename those text file with my name like

1.txt
2.txt
3.txt

After running command's it will look like this

Catchitbaby1.txt
Catchitbaby2.txt
Catchitbaby3.txt

For this I would cd to the folder containing the files and do:
rename s/^/Catchitbaby/ *txt

---

### Post by CatchItBaby on 2010-02-28
Now if i want to do reverse this process how to do?

means i want to remove Catchitbaby from the files

---

### Post by cjhabs on 2010-02-28
It is using Perl style regular expressions, so it would be:
rename s/^Catchitbaby// *.txt

s = search
/^Catchitbaby = a string starting with (^) Catchitbaby
// = replace with nothing
*.txt = do it for all files ending in .txt

---

### Post by CatchItBaby on 2010-02-28
Thanks a lot Nice Explanation

---

