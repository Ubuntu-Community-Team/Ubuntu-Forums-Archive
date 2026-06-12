---
title: "awk output file size limit (big files are truncated to 4.0kb)"
date: 2009-11-29
forum: General Help
---

### Post by LordNibler on 2009-11-29
Hi!

I'm trying to write a shell script that inserts Google counter code into html pages that are located in different folders. It works with small files (<4kb), but it truncates output of big files to 4.0kb. 

How can I process big files (>4.0kb) with awk? I'm very new to awk and scripting.

Script code:

```

#!/bin/bash
FILEDATE=`date "+%Y-%m-%d_%H-%M"`
export reptext=`cat google-counter-test.txt`
export repbegin="<!-- GOOGLE COUNTER BEGIN -->"
export repend="<!-- GOOGLE COUNTER END -->"
export repsearch="</body>"
for fname in `find . -name "*.html"`
do
cp $fname $fname-$FILEDATE.bak
awk '{gsub(ENVIRON["repsearch"],"\n"ENVIRON["repbegin"]"\n"\
ENVIRON["reptext"]"\n"\
ENVIRON["repend"]"\n"\
ENVIRON["repsearch"]"\n",$0); print > FILENAME}' $fname
done

```

Can anybody help me?

Thanks.

---

### Post by openuniverse on 2009-12-07
.

---

### Post by abcuser on 2009-12-07
LordNibler, have you tried using sed command?

---

### Post by LordNibler on 2009-12-08
**openuniverse** and **abcuser**, thank you for your replies!

> **openuniverse said:**
> my guess (because i'm as new to awk as you) is that this is an issue with the pipe | instead of awk.

sudo apt-get install curl ; echo $(curl [http://en.wikipedia.org](http://en.wikipedia.org)) | awk '{print $_}' doesn't truncate 40k of text on a single line


It is not 40k, it is 4 kilobytes.

> **openuniverse said:**
> 
(or on separate lines if you change "echo $(curl http://en.wikipedia.org)" to just "curl http://en.wikipedia.org")

edit: except you're not using a pipe, hmm...

Yes, I'm not using pipe.

> **abcuser said:**
> LordNibler, have you tried using sed command?

No, I've not tried sed. Unfortunately, I don't know its syntax yet.

I changed the code and it seems to work:
```

#!/bin/bash
FILEDATE=`date "+%Y-%m-%d_%H-%M"`
export reptext=`cat google-counter-test.txt`
export repbegin="<!-- GOOGLE COUNTER BEGIN -->"
export repend="<!-- GOOGLE COUNTER END -->"
export repsearch="</body>"
for fname in `find . -name "*.html"`
do
cp $fname $fname-$FILEDATE.bak
awk '{gsub(ENVIRON["repsearch"],"\n"ENVIRON["repbegin"]"\n"\
ENVIRON["reptext"]"\n"\
ENVIRON["repend"]"\n"\
ENVIRON["repsearch"]"\n",$0); print $0}' $fname > $fname.tmp
rm $fname
mv $fname.tmp $fname 
done

```

The difference is that I was writing to the opened file (print > FILENAME) in the previous version, in the last version a separate temporary file is created instead of it.

I don't know why the first version doesn't work...

Below is the code to undo the insertion:

```

#!/bin/bash
export repbegin="<!-- GOOGLE COUNTER BEGIN -->"
export repend="<!-- GOOGLE COUNTER END -->"
export repsearch="</body>"
for fname in `find . -name "*.html"`
do
awk '{  if ($0 == ENVIRON["repbegin"]) {k=1}; 
	if ($0 == ENVIRON["repend"]) {k=2; next}; 
	if (k == 1 ) {next}; 
	if (k != 1)  print $0}'  $fname > $fname.tmp
cp $fname.tmp $fname
rm $fname.tmp
done

```

It seems to work, but there can be mistakes...

---

