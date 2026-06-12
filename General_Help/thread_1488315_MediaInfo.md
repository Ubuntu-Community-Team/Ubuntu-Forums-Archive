---
title: "MediaInfo"
date: 2010-05-19
forum: General Help
---

### Post by domzz on 2010-05-19
I want to grab information from mediainfo and output it to a file with text already in it.

How would I do that?

```
        
#declaring the variables


filename=$1
DATE=`mediainfo "$filename" | grep "Recorded date" | awk -F" : " '{ print $2 }' | tr -d '\r' | sed -e 's/ /\_/' | rev | cut -b 10- | rev`
        TIME=`mediainfo "$filename" | grep "Recorded date" | awk -F" : " '{ print $2 }' | tr -d '\r' | sed -e 's/ /\_/' | cut -b 12- | rev | cut -b 4- | rev`
	LONGDATE=`date -d "$DATE" "+%B %d, %Y"`
	LONGTIME=`date -d "$TIME" "+%l:%M %p" |  sed -e 's/^[ \t]*//'`
	DURATION=`ffmpeg -i "$filename" 2>&1 | awk '/Duration:/{$4 gsub(/\:/," ") ;realseconds= $4; seconds = int($4); minutes= $3 ;hours= $2;totalsoundtrack = (seconds+(minutes*60)+(hours*3600)) $8 } END { print hours ":" minutes ":" realseconds}' | rev | cut  -b 5- | rev`
	ASPECT=`mediainfo "$filename" | grep "Display aspect ratio" | awk -F" : " '{ print $2 }' | tr -d '\r' | sed -e 's/[/]/\:/'`

MKVNAME="$DATE"_"$TIME"


### Create an XBMC-compliant .nfo file
echo "<episodedetails>
        <title>$LONGDATE - $LONGTIME</title>
        <rating></rating>
        <season></season>
        <episode></episode>
        <plot>This video was recorded on $LONGDATE at $LONGTIME.</plot>
        <credits></credits>
        <director></director>
        <aired>$DATE</aired>
	<time>$TIME</time>
	<runtime>$DURATION</runtime>
</episodedetails>" > "${MKVNAME}".nfo

echo "" >> "${MKVNAME}".nfo
echo "========== ORIGINAL FILE INFO ==========" >> "${MKVNAME}".nfo
echo "" >> "${MKVNAME}".nfo

mediainfo "$filename" >> "${MKVNAME}".nfo



```

---

### Post by papibe on 2010-06-17
I was wondering the same thing. I found this helpful post from andrew.46:

[http://ubuntuforums.org/showpost.php?p=8772052&postcount=5]("http://ubuntuforums.org/showpost.php?p=8772052&postcount=5")

I'm going to give it a try.

Regards.

---

