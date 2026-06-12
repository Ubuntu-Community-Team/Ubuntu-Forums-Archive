---
title: "how to detect text file in bash script"
date: 2009-12-09
forum: General Help
---

### Post by tacitdynamite on 2009-12-09
hello all, 

is there a command that can tell you if a certain file is plaintext or not?  my plaintext files don't necessarily end with a certain suffix.  i thought about using 'enca,' but that seems to be more oriented toward discovering the encoding of a file you already know to be a textfile.

like many, i try to keep my important files in plaintext, so i can quickly sync them across computers and view them in vim.  for a while i've had a reference directory that separates mixed media from text only files, to make detecting the text files easier: 

```
ref
|-- mix
|   |-- ebooks
|   `-- letters
`-- txt
    |-- bash
    |-- configuration
    |-- ebooks
    |-- journal
    `-- letters
```i'd rather not have to manually segregate my text files like this. i'd rather my reference folder look like this ...

```
ref
|-- bash
|-- configuration
|-- ebooks
|-- journal
`-- letters
```... and then use a command to pull out all the text files for quick grepping, syncing, and vimming. 

any ideas?

---

### Post by t0p on 2009-12-09
The command **file** determines file type.  For instance, the file '20014' is a JPEG image file.

```
t0p@phobos:~$ file 20014
20014: JPEG image data, JFIF standard 1.01

```

Whereas the file 'dxm' is a text file.

```
t0p@phobos:~$ file dxm
dxm: UTF-8 Unicode text

```

So you could use the *file* command, then *grep* the output for the string 'text'.

---

### Post by tacitdynamite on 2009-12-11
perfect. you're a jem. thanks so much.

---

