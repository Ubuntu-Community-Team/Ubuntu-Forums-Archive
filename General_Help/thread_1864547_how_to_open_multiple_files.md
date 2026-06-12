---
title: "how to open multiple files?"
date: 2011-10-19
forum: General Help
---

### Post by l3ecl on 2011-10-19
This is a two part question:

1. how do i open multiple files of the same type inside the folder using the terminal?

2. how do i open all the files in the folder using the terminal?

i tried:

```
gnome-open *.pdf
```

to open all the pdf files inside the folder i am in, but it only opened one.

i'm wondering what i am doing wrong.

---

### Post by surfer on 2011-10-19
evince allows you to open more than one pdf from the command line:
```
$ evince *.pdf
```

and to check which files are selected by a bash wildcard you can always start with ls first:
```
$ ls *.pdf
```
and then open the files with the application of your choice (as evince above).

---

### Post by Bmonsterboy on 2011-10-19
You can use find to search for files of a particular filetype: ```

bmonsterboy@lolol:~$ find ~/*.pdf
/home/broy/heya.pdf
/home/broy/lol.pdf

```

edit: Lol! way too slow...

---

### Post by Paddy Landau on 2011-10-19
gnome-open does not accept more than one parameter, even though the manual says that it does.

Here's your solution.


[LIST=1]
[*]*how do i open multiple files of the same type inside the folder using the terminal?*
```
find -maxdepth 1 -name '*.pdf' -exec gnome-open {} ';'
```
[*]*how do i open all the files in the folder using the terminal?*
```
find -maxdepth 1 -exec gnome-open {} ';'
```
[/LIST]
EDIT: Be sure to include the quotes as shown.

If you remove [FONT=Fixedsys]maxdepth 1[/FONT], then it will open all files in the directory *and* its subdirectories.

You could use the commands [FONT=Fixedsys]ls[/FONT] and [FONT=Fixedsys]xargs[/FONT] instead, but that combination can break under very rare circumstances.

---

