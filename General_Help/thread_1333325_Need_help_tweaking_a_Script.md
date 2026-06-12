---
title: "Need help tweaking a Script"
date: 2009-11-21
forum: General Help
---

### Post by tymanthius on 2009-11-21
Ok, so I have this script that works ok for converting vid's to a nice format & size for my Droid.  But it will only do 1 file at a time, and isn't very flexible.

What I would really like is someone who is good at scripting to take a look at it, and rework it so that I can do this:

```

DroidEncTest.sh /inputDir/* *.mp4

```

That way I can drop all my vids into 1 directory, and convert them as a batch.  Or even set this up as a cron command so that it will check my default dir nightly & convert.

The output dir will be 'hard coded' into the script.  actually, it is.  If you want, you can hard code the input dir too.  I'm ok with that.

Anyway, ANY help is appreciated.  Right now I'm having to manually run this script for each file, and that's kinda a pain.

---

### Post by lloyd_b on 2009-11-21
I'm having a hard time understanding your various commands (I'm not familiar with mencoder at all), but here's a simple framework to get you started:```
#!/bin/bash

# Set IFS, so that files with spaces in the name won't cause problems
# (provided that they're enclosed in quotation marks!)
IFS=$'\n'

# Loop through the command line arguments
for FILE in $*; do
    echo "$FILE"
done
```What this will do is take the command line arguments (no matter how many of them there are), and loop through them, displaying each one, one per line.

This could be invoked as "script file1.mp4 file2.mp4 file3.mp4" or using wildcards as in "script *.mp4".  Note that spaces in filenames will cause the loop mechanism to go wacky, unless the filenames are enclosed in quotation marks.  This means you don't have to worry about "input directory", since you can simply specify the full file path.

If you take your logic, and put it in between the "for..." and "done" statements, using $FILE for where you need the input filename, it should give you what you want.

Lloyd B.

---

### Post by tymanthius on 2009-11-21
Awesome.  I will try this out soon.

I don't really understand the mencoder stuff either, this is something the h264enc script spit out.  

But it seems like what you gave me may well work.

Thanks.

---

### Post by Bonster on 2009-11-21
Heres mine is bad but it works great with my crontab to convert to mp4.

Basically it goes into the folder i choose, then the converted files goes to my ipod folder. But if the file exist already it will skip and not convert those again.


> #!/bin/sh
# whereis /usr/local/bin/ffmpeg
# /home/heoyea/Public/scripts/crontab/korntab.sh > /tmp/krontab.log 2>&1
mkdir ~/Storage/.blackbox/ipod
cd ~/Storage/.blackbox/stock/Superstar

#AVI
for MOVIE in *.avi ; do

    echo Processing "$MOVIE"

    echo N | /usr/local/bin/ffmpeg -i "$MOVIE" -f mp4 -vcodec libxvid -subq 5 -refs 3 \
         -bt 700 -bf 0 -level 13 -maxrate 768 \
         -b 700  -qmin 3 -qmax 5 -bufsize 8192 -mbd 2 -cmp 2 \
         -subcmp 2 -g 300 -r 29.976023976 -acodec libfaac -ac 2 -ar 48000 \
         -ab 128 -s 320x240 -aspect 4:3 \
         ~/Storage/.blackbox/ipod/"$MOVIE.mp4"

done


#WMV
for MOVIE in *.wmv ; do

    echo Processing "$MOVIE"

    echo N | /usr/local/bin/ffmpeg -i "$MOVIE" -f mp4 -vcodec libxvid -subq 5 -refs 3 \
         -bt 700 -bf 0 -level 13 -maxrate 768 \
         -b 700  -qmin 3 -qmax 5 -bufsize 8192 -mbd 2 -cmp 2 \
         -subcmp 2 -g 300 -r 29.976023976 -acodec libfaac -ac 2 -ar 48000 \
         -ab 128 -s 320x240 -aspect 4:3 \
         ~/Storage/.blackbox/ipod/"$MOVIE.mp4"

done


#MPG
for MOVIE in *.mpg ; do

    echo Processing "$MOVIE"

    echo N | /usr/local/bin/ffmpeg -i "$MOVIE" -f mp4 -vcodec libxvid -subq 5 -refs 3 \
         -bt 700 -bf 0 -level 13 -maxrate 768 \
         -b 700  -qmin 3 -qmax 5 -bufsize 8192 -mbd 2 -cmp 2 \
         -subcmp 2 -g 300 -r 29.976023976 -acodec libfaac -ac 2 -ar 48000 \
         -ab 128 -s 320x240 -aspect 4:3 \
         ~/Storage/.blackbox/ipod/"$MOVIE.mp4"

done


#MPEG
for MOVIE in *.mpeg ; do

    echo Processing "$MOVIE"

    echo N | /usr/local/bin/ffmpeg -i "$MOVIE" -f mp4 -vcodec libxvid -subq 5 -refs 3 \
         -bt 700 -bf 0 -level 13 -maxrate 768 \
         -b 700  -qmin 3 -qmax 5 -bufsize 8192 -mbd 2 -cmp 2 \
         -subcmp 2 -g 300 -r 29.976023976 -acodec libfaac -ac 2 -ar 48000 \
         -ab 128 -s 320x240 -aspect 4:3 \
         ~/Storage/.blackbox/ipod/"$MOVIE.mp4"

done


#FLV
for MOVIE in *.flv ; do

    echo Processing "$MOVIE"

    echo N | /usr/local/bin/ffmpeg -i "$MOVIE" -f mp4 -vcodec libxvid -subq 5 -refs 3 \
         -bt 700 -bf 0 -level 13 -maxrate 768 \
         -b 700  -qmin 3 -qmax 5 -bufsize 8192 -mbd 2 -cmp 2 \
         -subcmp 2 -g 300 -r 29.976023976 -acodec libfaac -ac 2 -ar 48000 \
         -ab 128 -s 320x240 -aspect 4:3 \
         ~/Storage/.blackbox/ipod/"$MOVIE.mp4"

done

#Play A Sound
mplayer -msglevel all=-1 ~/Public/soundbits/theforcewillbewithyoualways.wav

---

### Post by tymanthius on 2009-11-21
I see you are usinf ffmpeg. I can't get that to work for me. I'm using Karmic and aac in ffmpeg is broken.  I even compiled from source and the results were unusable.

But I may see if I can adapt your script to mine.

---

### Post by andrew.46 on 2009-11-22
Hy tymanthius,

> **tymanthius said:**
> I see you are usinf ffmpeg. I can't get that to work for me. I'm using Karmic and aac in ffmpeg is broken.  I even compiled from source and the results were unusable.

Rather than *broken* aac encoding has been deliberately *removed* by the packagers :cry:. If you are having trouble compiling FFmpeg from source perhaps this guide might help you out:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

All the best,

Andrew

---

### Post by tymanthius on 2009-11-22
> **andrew.46 said:**
> Hy tymanthius,



Rather than *broken* aac encoding has been deliberately *removed* by the packagers :cry:. If you are having trouble compiling FFmpeg from source perhaps this guide might help you out:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

All the best,

Andrew

I tried that.  The results I got would play at about 1 frame a second or two, and jumped.  Audio was usually good though.

The mencoder based solution I found is working, so I'm happy.

---

