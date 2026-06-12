---
title: "Convert .cbr to .cbz"
date: 2009-09-23
forum: General Help
---

### Post by Ankhwatcher on 2009-09-23
Hey, I have a Comic book reader called [TouchComic]("http://code.google.com/p/touchcomic/downloads/list") for my phone, and I want to read comics on it. (Naturally enough)
Unfortunately it only reads .cbz (comic book zip) or .zip files and most of my comic books are in .cbr (comic book rar) format.

Manually converting them is a fairly simple process, but it's annoyingly slow and labour intensive.
How can I create a script that will automatically convert them for me? (7zip happily opens both, and creates zips/cbz)

thanks,
-ANkh

---

### Post by Jonathan Harford on 2009-11-28
I'm using this bash script to do the conversion:
[http://www.kingbin.net/blog/2009/11/03/285/](http://www.kingbin.net/blog/2009/11/03/285/)

Other than replacing spaces with underscores, it seems to work pretty great.

---

### Post by Ankhwatcher on 2009-11-28
> **Jonathan Harford said:**
> I'm using this bash script to do the conversion:
[http://www.kingbin.net/blog/2009/11/03/285/](http://www.kingbin.net/blog/2009/11/03/285/)

Other than replacing spaces with underscores, it seems to work pretty great.

 That sounds great, thanks!

---

### Post by Jonathan Harford on 2009-12-28
Now I see that *some* of the CBZs I've converted contain the original CBRs *inside* them, making them over twice as big as the CBRs! Grrr.

---

### Post by albins on 2010-01-16
I made a slightly improved version of the script. This one requires the proprietary "unrar" binary, like the older one, but it should not put cbr files inside cbz. Also, it takes one file at a time; you can use a simple for loop yourself! ```
for a in *.cbr;do cbr2cbz "$a";done
``````

#bin/bash

cbr=$1
start_directory=`pwd`

cbz=`basename "$cbr" .cbr`.cbz

tempdir=`mktemp -d`
cd "$tempdir"
unrar e -inul "$start_directory/$cbr"
zip -q "$start_directory/$cbz" *
rm -rf "$tempdir"

```Also, it doesn't change file names (except replacing .cbr with .cbz of course), and uses a generated temporary folder in /tmp/ instead of a fixed name. And it doesn't copy around the files like the previous one; unrar will extract to the current directory, there's no need for any copying.

---

### Post by wattana on 2010-08-11
Hi Albins!

Thanks a lot for your script. It works like a charm!

:D

---

