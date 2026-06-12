---
title: "Insert a forward slash &quot;/&quot; into a variable in bash script"
date: 2010-06-19
forum: General Help
---

### Post by kjrunner on 2010-06-19
I'm sure this is uber simple, but I've been searching and trying things for over 4 hours now. I need to insert a forward slash "/" into a text string in a bash script.

I am trying to get the script to read in a variable (comes from a file) and then add a forward slash and then a subdirectory name so it can be created.

Currently:

```
startdir=$PWD #($PWD=mnt/Pictures)
subdir=Summer10/Mexico
thumbdir=$startdir/$subdir/thumb
echo $thumbdir

#mkdir $thumbdir #eventually the code I actually want to use
```


Output is: "/thumbictures/Summer10/Mexico"

The desired output is: "/mnt/Pictures/Summer10/Mexico/thumb"

Appreciate any and all help. 

Thanks-

KJ

---

### Post by fragos on 2010-06-19
Try proceeding with a "\" as in "\/"

---

### Post by geirha on 2010-06-19
You are doing it right, (apart from lacking quotes for echo and mkdir's args), but the file you read the dirs from probably has dos line-endings. When you print a \r in linux, it moves to the start of the line.
```
$ printf "ab\rc\n"
cb

```
See [http://mywiki.wooledge.org/BashFAQ/052](http://mywiki.wooledge.org/BashFAQ/052) on how to deal with that.

---

### Post by kjrunner on 2010-06-19
Thank you for the quick replies.

Looks like my problem was occurring from the "\n" issue with the dos created text file importing the directory names from. Thank you for pointing this out. (Edited to show code actually used)

I changed the import code from:

```
subdir=$(`cat "dir.txt")
```

To:

```
txtin=$( tr -d '\r' < dir.txt)
declare -a subdir
subdir=($txtin)

```

The code used now works, probably not the proper way to do it. Will be looking at cleaning the code up. The website geirha provided a link to was very useful. The website linked to in geirha next link is also useful. 

Thanks again.

---

### Post by geirha on 2010-06-20
> **kjrunner said:**
> 
```
subdir=$( tr -d '\r' < dir.txt)
```


If that file, dir.txt, contains more than one filename, that's the wrong way to read it. See [How can I read a file (data stream, variable) line-by-line (and/or field-by-field)?](http://mywiki.wooledge.org/BashFAQ/001)

---

