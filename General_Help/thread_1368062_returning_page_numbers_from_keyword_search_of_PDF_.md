---
title: "returning page numbers from keyword search of PDF files"
date: 2009-12-30
forum: General Help
---

### Post by GOwin on 2009-12-30
I've already found this thread: [url=http://ubuntuforums.org/showthread.php?t=1051658]Search a keyword in many PDF documents at the same time, is it possible?[/ur] where:

```
ls *.pdf | xargs -I{} pdftotext {}  - | grep "keyword"
```

Is there a way to get the page numbers of the keyword hits?

---

### Post by kaibob on 2009-12-30
> **GOwin said:**
> Is there a way to get the page numbers of the keyword hits?

I do not know of any modification to the command-line in your post that will show the page number of search-string matches. Perhaps another forum member will be able to help with this.

Just to practice, I wrote the following shell script, which is a bit involved but does what you want. The user enters the search string as a command-line parameter, and the script returns the page number and file name of any search-string matches. 

This shell script uses the pdfinfo utility. If not already installed, it's available in the repo's as part of poppler-utils and xpdf-utils packages.

```
#!/bin/bash

[ "$*" ] || { echo "You forgot a search string!" ; exit 1 ; }

found=1

for file in *.pdf ; do
   [ "$file" = '*.pdf' ] && echo "No PDF files found!" && exit 1
   pages=$(pdfinfo "$file" | awk '/Pages:/ { print $NF }')
   for ((i=1 ; i<=$pages ; i++)) ; do
      match=$(pdftotext -q -f $i -l $i "$file" - | grep -m 1 "$*")
      [ "$match" ] && echo "Page $i in $file" && found=0
   done
done

[ "$found" -ne 0 ] && echo "No search string matches found"
```

---

### Post by GOwin on 2009-12-30
Thank you!

Easy is nice but even if it's slow I'm not complaining as long as it works. ;-)

The alternative is worse: searching each file by hand.

---

### Post by kaibob on 2009-12-30
I wanted to adapt the shell script for my own use and thought I would post the result just in case another forum member happens upon this thread. The changes include the use of the find command to make searches recursive; modifying the code to work with the dash shell; adding the -i option to grep to make searches case insensitive; and improved output formatting. 

```
#!/bin/sh

[ "$*" = "" ] && printf "\nYou forgot a search string!\n\n" && exit 1

oldfile=xxx

find $PWD -iname "*.pdf" -type f | 
{
while read file ; do
   pages=$(pdfinfo "$file" | awk '/Pages:/ { print $NF }')
   for i in $(seq ${pages}) ; do
      match=$(pdftotext -nopgbrk -q -f $i -l $i "$file" - | \
         fgrep -i -w -c -m 1 "$*")
      if [ "$match" -eq 1 ] && [ "$file" != "$oldfile" ] ; then
         printf "\n\n$file\n"
         printf "Page"
         oldfile="$file" 
      fi
      [ "$match" -eq 1 ] && printf " $i "
   done
done

[ "$oldfile" = xxx ] && printf "\nNo matches!"
}

printf "\n\n"
```

---

### Post by GOwin on 2009-12-30
Kaibob, many thanks for keeping at it.

Tried both your versions and time results are as follows:

original bash script
real	55m11.625s
user	25m21.730s
sys	18m4.730s

revised dash script:
real	76m50.941s
user	31m17.670s
sys	20m3.320s

I ran both scripts with the same set of PDFs but my time results are opposite yours. It actually took a bit longer.

---

### Post by kaibob on 2009-12-31
You must be searching an enormous number of PDF files. My test searches, which involved what I considered to be a large number of PDF files, took around 30 seconds, and that's on a 6-year-old computer.

I guess the timing varies depending on the PDF files and the computer. I suspect your results are more valid.

---

### Post by GOwin on 2009-12-31
Yes, more than a handful. :D Each file could be more than 400 pages long.

I'm still wondering if it's at all possible to get page numbers directly off the PDF files when the keyword is found. Your present technique, though it works, had to slog through all the pages. 

Usually I only need to take about 20-30 pages from every file.

I haven't found out how though, but your script works! Thanks a lot and a happy new year.

---

### Post by Eric Boring on 2012-09-20
I know this is an old post, but you just saved me HOURS of work on my dissertation! THANK YOU!

---

