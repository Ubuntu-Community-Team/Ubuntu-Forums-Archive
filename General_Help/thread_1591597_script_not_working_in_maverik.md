---
title: "script not working in maverik"
date: 2010-10-09
forum: General Help
---

### Post by sn0m on 2010-10-09
Hi guys
I've installed maverik instead of the old one which is due to expire tonight and to my bad suprise I found my little script for converting video files to nokia format not working.
This is the script:
#!/bin/bash
FILE=""
DIR="/home/koli/dwhelper"
if [ "$(ls -A $DIR)" ]; then
cd $DIR
#check for flv and do convert to mp3 as well as mp4 and move them to respective folders
   for i in *.flv ; do ffmpeg -i "$i" -acodec copy "$i".mp3 > /dev/null 2>&1 ; done
sleep 3s
for i in *.flv ; do ffmpeg -i "$i" -f mp4 -vcodec libxvid -s 640x360 -b 768kb -r 25 -aspect 16:9 -acodec libfaac -ab 96kb -ar 44100 -ac 2 "$i".mp4 > /dev/null 2>&1 ; done
sleep 3s &&
#check for wmv and do convert to mp3 as well as mp4 and move them to respective folders
for i in *.wmv ; do ffmpeg -i "$i" -f mp4 -vcodec libxvid -s 640x360 -b 768kb -r 25 -aspect 16:9 -acodec libfaac -ab 96kb -ar 44100 -ac 2 "$i".mp4 > /dev/null 2>&1 ; done
 sleep 2s
for i in *.asf ; do ffmpeg -i "$i" -f mp4 -vcodec libxvid -s 640x360 -b 768kb -r 25 -aspect 16:9 -acodec libfaac -ab 96kb -ar 44100 -ac 2 "$i".mp4 > /dev/null 2>&1 ; done
 sleep 3s
 mv *.mp3 /home/koli/Music/mp3_radio_files
  mv *.mp4 /home/koli/videofornokia 
   mv *.wmv /home/koli/videoforlaptop
    mv *.flv /home/koli/videoforlaptop
else
 exit
fi

It works fine for flv files but not for wmv ones.
I get this message: Unknown encoder 'libfaac' and when I check on synaptic the libfaac is installed ok.....is this a bug of some sort?
Can someone help me with it or do I need to go back to karmic...
Thanks in advance
sokol

---

### Post by mc4man on 2010-10-09
The default ubuntu ffmpeg does not have aac encoding enabled. (hasn't for awhile
Either build your own ffmpeg or wait for medibuntu to open a maverick repo and upgrade to their 'extra' versions of the ffmpeg shared libs

---

### Post by andrew.46 on 2010-10-11
Hi mc4man,

> **mc4man said:**
> Either build your own ffmpeg or wait for medibuntu to open a maverick repo and upgrade to their 'extra' versions of the ffmpeg shared libs

They appear to be open for business but I believe they have shifted servers and it will take a while for all of their addresses to settle down, hence a lot of 404 messages.

Andrew

---

