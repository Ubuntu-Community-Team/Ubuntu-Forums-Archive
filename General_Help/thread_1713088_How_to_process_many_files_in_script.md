---
title: "How to process many files in script?"
date: 2011-03-23
forum: General Help
---

### Post by moltek on 2011-03-23
I have a number of files in a folder:
```
media@serwer ~/test $ ls
FileA.txt  FileB.txt  File 1.txt  File 2.txt  File 3.txt

```These files are encoded in codepage WIN1250 and I want to convert them to UTF8 using this script (executing it 'conv *'):
```
#!/bin/bash
for file in $1; do
    if [ -f $file ]; then
       echo $file
       iconv -f WINDOWS-1250 -t UTF8 -o $file.utf $file
    fi
done
exit 0
```However it only renames the first file when it has no spaces in its name.
How should I modify it to accept wildcards and to process files with spaces in filename?

Thanks for help!!!

---

### Post by WorMzy on 2011-03-23
You need to glob all over it.

Er. I mean, like this:

```
for file in /path/to/folder/*; do
  iconv -f WINDOWS-1250 -t UTF8 -o "$file".utf "$file"
done
```

---

### Post by moltek on 2011-03-23
Thanks, it helped with filenames containing spaces.

The script now:
```
#!/bin/bash
for file in "$1"; do
    if [ -f "$file" ]; then
       echo "$file"
       iconv -f WINDOWS-1250 -t UTF8 -o "$file".utf "$file"
    fi
done
exit 0
```When I replace [FONT=Courier New]"$1"[/FONT] with [FONT=Courier New]*[/FONT] in the second line script works as I want it to. In the form above the script processes only [FONT=Courier New]FileA.txt[/FONT] though

The problem now is that there is [COLOR=Blue]_[filename expansion]("http://www.gnu.org/software/bash/manual/bashref.html#Filename-Expansion")_[/COLOR]. Variable should be replaced with a list of variables but my script only processes the first item on the list.

More ideas?

---

### Post by sisco311 on 2011-03-23
```
for file in "$@"
do
...

```

EDIT:

See:
```
man bash | less +/"^ +Special Parameters"
```

---

### Post by SeijiSensei on 2011-03-23
Change to the directory where the files are located, and use this instead:

```
for file in *.txt
```

That will iterate over all .txt files in the current directory.  If you want a more generalizable version, you can specify a directory of files to convert in the command line and pass it as $1 to the script:

```

cd $1
for file in *.txt
do
[...]

```

---

### Post by moltek on 2011-03-23
That's the solution:
```
#!/bin/bash
for file in "$@"; do
    if [ -f "$file" ]; then
       echo "$file"
       iconv -f WINDOWS-1250 -t UTF8 -o "$file".utf "$file"
    fi
done

exit 0
```

Thanks a lot for your help!!

---

### Post by sisco311 on 2011-03-23
You're welcome!

BTW, **for file** is equivalent to **for file in "$@"**. Just in case you are `lazy' to type the extra characters.  :)

---

