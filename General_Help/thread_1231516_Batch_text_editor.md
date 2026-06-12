---
title: "Batch text editor?"
date: 2009-08-04
forum: General Help
---

### Post by ezekiel000 on 2009-08-04
I have a load of html files that I would like to batch convert to plain text by stripping out everything except the plain text content. e.g. remove everything before a certain tag and after a certain tag and change <br /> to a carriage return.

Is there any program or script that can help me with this?

---

### Post by llamabr on 2009-08-04
```
brock@hops:~$ apt-cache search html2text
html2text - advanced HTML to text converter
brock@hops:~$ 

```

---

### Post by ezekiel000 on 2009-08-04
What sort of command/options etc would I run to get it to do what I asked? As I had a look at it before but I couldn't see a way to do what I want.

---

### Post by llamabr on 2009-08-04
how many html files do you want to edit?  If only a few, it looks like you do:

```
html2text file.html file.txt
```

If hundreds, or whatever, you could write a simple script to do it.

---

### Post by ezekiel000 on 2009-08-04
I've got 1550 files to convert. (I'm not very good a writing scripts unless I follow or modify a tutorial)

Will that allow me to cut everything before a specified html tag and everything after a specified tag?

---

### Post by llamabr on 2009-08-04
Hmm.  You want to find certain bits INSIDE OF some html files, and convert that bit to text, leaving the rest of the html files intact?  Probably that will not do it, then.

Again, a script could be written to do this, though when I try to do so I always get something wrong.

---

### Post by ezekiel000 on 2009-08-04
I should probably explain more, I've got 1550 html files saved from a lyrics website, I would like just the lyrics in plain text, so:
- remove everything before and including "<div class='lyricbox' >"
- remove everything after and including "<p><!-- "
- replace "<br />" with "\n"

---

### Post by martinbaselier on 2009-08-04
This will do the trick:

Go to the directory where the html files are. 

Then this command will do the trick. 
**find * -name "*.html" -exec html2text {} {}.text \;**

This will create files *.html.text from *.html


-name "*.html" will only use any file named *.html
-exec will execute a command. 
{} will be replaced by the file name


If you want all the lyrics in one file,

**find * -name "*.text" -exec cat {} \; > allthelyrics.text **
will do the trick.

---

### Post by ezekiel000 on 2009-08-04
That gave me a lot of cant find [file name].html.text
Also it doesn't look like it will cut out the unwanted bits of the files.
But thank you for trying to help.

---

### Post by martinbaselier on 2009-08-04
It seems the syntax of html2text is different than suggested above. 

This will create one big file with all lyrics:
find * -name "*.html" -exec html2text {} \; > allthelyrics.txt

This will create individual files:
find * -name "*.html" -exec html2text -o {}.text {} \;

---

### Post by ezekiel000 on 2009-08-04
Thank you that almost worked. (see attached) Is there anyway to automate the removal of the junk before and after the lyrics?

---

### Post by Glyndwr on 2009-08-04
> **ezekiel000 said:**
> Thank you that almost worked. (see attached) Is there anyway to automate the removal of the junk before and after the lyrics?

Here's a simple script to try.  I assumed your lyrics were marked by tags like:
<lyric>
</lyric>

This should create a whole lot of new files ending in .NEW that will just have everything between the tags.

#!/bin/bash
for i in *.html
do
echo working on $i
TMPFILE=$i.TMP
NEWFILE=$i.NEW

# remove the unwanted lines at the top
START=`grep -n "<lyric>" $i|cut -d: -f1`
sed -e "1,"$START"d"  $i > $TMPFILE

# remove the unwanted lines at the bottom
TOTAL=`wc -l $TMPFILE | cut -d' ' -f1`
STOP=`grep -n "</lyric>" $TMPFILE|cut -d: -f1`
sed -e ""$STOP","$TOTAL"d" $TMPFILE > $NEWFILE
done

---

### Post by ezekiel000 on 2009-08-05
The lyrics in these files seem to be sandwiched bettween <div class='lyricbox' > & <p><!-- 

So I edited your script and ended up with the original html, and empty new file and a temp file containing all the junk (see attached)

---

### Post by ezekiel000 on 2009-08-06
Any ideas?

---

### Post by martinbaselier on 2009-08-06
**man html2text** shows how to filter out the escaped characters: 

Here are the altered commands:

This will create one big file with all lyrics:
find * -name "*.html" -exec html2text -nobs {} \; > allthelyrics.txt

This will create individual files:
find * -name "*.html" -exec html2text -nobs -o {}.text {} \;

---

### Post by ezekiel000 on 2009-08-06
Thanks that'll do.

---

