---
title: "Youtube to mp3 bash"
date: 2010-02-04
forum: General Help
---

### Post by alket on 2010-02-04
I have made a bash script that downloads youtube flv file and converts it to mp3.
```

LINK="vHAvjaHtlMA"
MP3="wearefreenow"
youtube-dl http://www.youtube.com/watch?v=$LINK
ffmpeg -i $LINK.flv $MP3.mp3

```

but in this case I need to edit it manually adding to link variable *vHAvjaHtlMA* and to mp3 variable *wearefreenow* .
How can i make it to prompt me in terminal for input
```

Insert the link:
Insert the song name:

```

---

### Post by alket on 2010-02-04
SOLVED

```
echo -n "Youtube File: "
read -e LINK
echo -n "Song name: "
read -e MP3
youtube-dl http://www.youtube.com/watch?v=$LINK
ffmpeg -i $LINK.flv $MP3.mp3
```

---

### Post by whitethorn on 2010-02-04
This is a script I wrote to download youtube videos and convert them to mp3s.  How it works first it downloads the video converts it and puts the mp3 on the desktop then plays it using whatever system default you have for mp3s.

If you have a youtube account you can substitute username and passwort.  If not just get rid of the -u and -p.  To get it to work save the scripts somewhere get it executable copy a youtube link and run it as follows.

./youtubemp3 youtube-link.com...

```


#!/bin/bash
cd /tmp/
youtube-dl -l -b -u username -p password "$1"
a=`ls |grep flv`
c=`ls |grep mp4`
echo "It was saved to $a"
echo "It was saved to $c"
if [ -n $a ]; then 
d=`basename "$c" .mp4`
echo "Converting from  mp3 $d"
ffmpeg -i "$c" -acodec libmp3lame /home/$USER/Desktop/"$d".mp3
rm "$c"
echo "Converted from mp4"
gnome-open /home/$USER/Desktop/"$d".mp3
else
b=`basename "$a" .flv`
ffmpeg -i "$a" -acodec libmp3lame /home/$USER/Desktop/"$b".mp3
rm "$a"
echo "Converted from flv"
gnome-open /home/$USER/Desktop/"$b".mp3
fi

```

---

