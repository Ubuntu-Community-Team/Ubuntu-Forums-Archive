---
title: "Is there a variation of grep to search files for keywords?"
date: 2010-07-10
forum: General Help
---

### Post by wilwil0 on 2010-07-10
I know you can use grep to find keywords in filenames, but is there a variation that can enable you to search the content of the files themselves?

---

### Post by theozzlives on 2010-07-10
I believe it's sed that will find, replace, etc in text files.

> NAME
       sed - stream editor for filtering and transforming text

SYNOPSIS
       sed [OPTION]... {script-only-if-no-other-script} [input-file]...

DESCRIPTION
       Sed  is a stream editor.  A stream editor is used to perform basic text
       transformations on an input stream (a file or input from  a  pipeline).
       While  in  some  ways similar to an editor which permits scripted edits
       (such as ed), sed works by making only one pass over the input(s),  and
       is consequently more efficient.  But it is sed's ability to filter text
       in a pipeline which particularly distinguishes it from other  types  of
       editors.


---

### Post by Vaphell on 2010-07-10
strange, i grep files for content just fine

grep "phrase to be found" <files>

-i if the search is to be case insensitive
-r if recursive

read help section of grep to get more info

---

### Post by audiomick on 2010-07-10
As far as I know, it is
```
find
```
that searches file names, and grep searches for character strings in a text file.

Have you looked at the manual page?
```
man grep
```

I can't tell you exactly how to use it, because I never have. I have only read about it.

---

### Post by patchwork on 2010-07-10
Depending on the content of the file, you can try to grep a binary file as text using the -a option.  I have had mixed results using this though.

---

### Post by wilwil0 on 2010-07-10
> **Vaphell said:**
> strange, i grep files for content just fine

grep "phrase to be found" <files>

-i if the search is to be case insensitive
-r if recursive

read help section of grep to get more info

What should I put in ,files., the name of every file I'm searching or the directory?

---

### Post by patchwork on 2010-07-10
for multiple files:
```
grep -e PATTERN -f FILE1 FILE2 etc
```
or
```
grep -r PATTERN DIRECTORY
```

The man pages contain the full list of options
```
man grep
```

---

### Post by wilwil0 on 2010-07-10
SO if I wanted to search for the word, say, apples, in /home/will/Music (that also has many subdirectories) the command would  be:
> grep -i -r "apples" /home/will/Music


?

---

### Post by wilwil0 on 2010-07-10
It does work, thanks guys.

---

### Post by HermanAB on 2010-07-10
There is also fgrep.

---

