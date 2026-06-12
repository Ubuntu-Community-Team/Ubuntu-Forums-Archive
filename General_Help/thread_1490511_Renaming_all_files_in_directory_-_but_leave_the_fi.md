---
title: "Renaming all files in directory - but leave the file extension alone"
date: 2010-05-22
forum: General Help
---

### Post by rugbert on 2010-05-22
OK, how can I rename all files in a directory up to the first dot (there by leaving the file extension alone) to the same thing?

Im trying to rename all my media files and associated files in a directory to (preferably) the name of the directory it self.

so if I have 

```
A Clockwork Orange - 
    wzzyfg.cd1.avi
    wzzyfg.cd2.avi
    wzzyfg.nfo
    ACO.fanart.jpg
    orange.tbn
```

Id like to automatically mass rename them all to 

 
```
A Clockwork Orange
    A Clockwork Orange.cd1.avi
    A Clockwork Orange.cd2.avi
    A Clockwork Orange.nfo
    A Clockwork Orange.fanart.jpg
    A Clockwork Orange.tbn
```

I have rename on my server which I used to remove underscores from file names, but I dont know how I would use it to rename everything up to the first period.

Bonus points for renaming stuff to the name of the parent folder!

---

### Post by jamesisin on 2010-05-22
You can do certain replacements using a for loop in BASH, but this won't work for all the files because they don't all have the same string in them.  You may have to make some piecemeal concessions.  Have a look at this script I use for prepending album numbers to track names:

[http://www.soundunreason.com/InkWell/?p=1415](http://www.soundunreason.com/InkWell/?p=1415)

You can replace the *.flac with the/folder/path and that should act on all files regardless of extension.

---

### Post by lhowaf on 2010-05-22
I use pyRenamer for this kind of job. I'd give you search help  but last time I did that, my post was jailed.

---

### Post by kaibob on 2010-05-22
I believe the following will do what you want.   I have only tested it with the files given in your post, so be sure to work with copies. And, make absolutely sure that you are in the correct directory--otherwise this command could do a lot of harm. Just as a precaution, I have used the copy rather than the move command.

```
for file in * ; do cp  "$file" "${PWD##*/}.${file#*.}" ; done
```


> $ echo $PWD
/home/kaibob/temp/A Clockwise Orange

$ ls -1
ACO.fanart.jpg
orange.tbn
test 1.cd3.avi
wzzyfg.cd1.avi
wzzyfg.cd2.avi
wzzyfg.nfo

$ for file in * ; do mv  "$file" "${PWD##*/}.${file#*.}" ; done
$

$ ls -1
A Clockwise Orange.cd1.avi
A Clockwise Orange.cd2.avi
A Clockwise Orange.cd3.avi
A Clockwise Orange.fanart.jpg
A Clockwise Orange.nfo
A Clockwise Orange.tbn

---

### Post by sq7bti on 2010-05-22
```

NAME
       rename - renames multiple files

SYNOPSIS
       rename [ -v ] [ -n ] [ -f ] perlexpr [ files ]

DESCRIPTION
       "rename" renames the filenames supplied according to the rule specified as the first argument.  The perlexpr argument is a
       Perl expression which is expected to modify the $_ string in Perl for at least some of the filenames specified.  If a
       given filename is not modified by the expression, it will not be renamed.  If no filenames are given on the command line,
       filenames will be read via standard input.

       For example, to rename all files matching "*.bak" to strip the extension, you might say

               rename 's/\.bak$//' *.bak

       To translate uppercase names to lower, you'd use

               rename 'y/A-Z/a-z/' *

```NAME

---

### Post by dfreer on 2010-05-22
A GUI approach would be to use Thunar File Manager's Bulk Rename tool, here's a screenshot of it in action:
[http://mcs.une.edu.au/doc/Thunar/html/eu/images/bulk-rename.png](http://mcs.une.edu.au/doc/Thunar/html/eu/images/bulk-rename.png)

I would use some variant of the "find" program in CLI to rename the files if needed.

---

