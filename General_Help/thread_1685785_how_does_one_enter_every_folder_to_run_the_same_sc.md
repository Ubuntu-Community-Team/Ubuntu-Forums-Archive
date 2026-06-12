---
title: "how does one enter every folder to run the same script in all of them?"
date: 2011-02-11
forum: General Help
---

### Post by shantiq on 2011-02-11
i have this script here which runs very well in any given flac folder


**but** I want to run it in four folders within a folder so i do not have to do it each time    i want to bulk convert

see image

so i have tried 

```
*/./flac2tak.sh

```                         the wildcard to enter each folder then the script

and a few other unsuccessful combinations



so what do i need to write to enter each folder and apply the script



thanx 


shan

---

### Post by DaithiF on 2011-02-11
```
for i in */
do
  cd "$i"
  ../flac2tak.sh
  cd ..
done
```

---

### Post by ajgreeny on 2011-02-11
Can we see the script/command itself please.

It possibly simply needs a "recursive" option (-r or -R) for the script's main command, but it would help to know what you are trying to do.

---

### Post by shantiq on 2011-02-11
> **DaithiF said:**
> ```
for i in */
do
  cd "$i"
  ../flac2tak.sh
  cd ..
done
```


thank you very much DaithiF works a charm


one day i shall be able to work this out myself:KS:KS



ps   ajgreeny   if there is an alternative way i would also be interested to see that


the script is (courtesy of mc4man)

```
#!/bin/bash
for f in *.flac
do
OUTF=`echo "$f" | sed s/\.flac$/.tak/g`


    ARTIST=`metaflac "$f" --show-tag=ARTIST | sed s/.*=//g`
    TITLE=`metaflac "$f" --show-tag=TITLE | sed s/.*=//g`
    ALBUM=`metaflac "$f" --show-tag=ALBUM | sed s/.*=//g`
    DATE=`metaflac "$f" --show-tag=DATE | sed s/.*=//g`
    GENRE=`metaflac "$f" --show-tag=GENRE | sed s/.*=//g`
    TRACKNUMBER=`metaflac "$f" --show-tag=TRACKNUMBER | sed s/.*=//g`

flac -c -d "$f" - | wine takc -e -pMax  -tt ARTIST="$ARTIST"  -tt TITLE="$TITLE"  -tt ALBUM="$ALBUM" -tt DATE="$DATE" -tt GENRE="$GENRE"  -tt TRACKNUMBER="$TRACKNUMBER"  - "$OUTF"
done
mkdir "$ALBUM" && mv *.tak "$ALBUM"
```

---

