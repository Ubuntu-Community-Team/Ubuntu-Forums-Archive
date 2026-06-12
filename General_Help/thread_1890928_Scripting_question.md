---
title: "Scripting question"
date: 2011-12-04
forum: General Help
---

### Post by Ubuntewbie on 2011-12-04
Greetings All, 
I am creating a quick little script for school to "replace" the rm command.

I found this following thread which gave me most of the logic I was looking for:
[http://ubuntuforums.org/showthread.php?t=780764](http://ubuntuforums.org/showthread.php?t=780764)

Here is what I have so far:
```
#!/bin/sh

if [ "$1" = "" ]; then
echo "No Arguments"

TARGET=~/.TRASH
DAY=`/bin/date '+%d'`
MONTH=`/bin/date '+%m'`
YEAR=`/bin/date '+%Y'`
DATE=$YEAR$MONTH$DAY

if [ ! -d $TARGET/$DATE ]
then
mkdir -p $TARGET/$DATE
fi

mv $1 $2 $3 $4 $5 $TARGET/$DATE


```My question is how do I append the date and time to the end of the file instead of dumping it into a dated directory?

In other words, I want the script to move "example.txt" to ~/.TRASH and name it "example.txt_20101231_2342"

Thanks so much for your help! :D

---

### Post by papibe on 2011-12-04
You would have to move each file individually. Something like this:
```
...
for file in "$@"
do
        mv "$file"   "$TARGET"/"$file"_"$DATE"
done
...
```
Hope it helps,
Regards.

---

### Post by Ubuntewbie on 2011-12-05
> **papibe said:**
> You would have to move each file individually. Something like this:
```
...
for file in "$@"
do
        mv "$file"   "$TARGET"/"$file"_"$DATE"
done
...
```
Hope it helps,
Regards.

Thanks! That worked perfectly! :-P

---

