---
title: "script not working"
date: 2010-02-12
forum: General Help
---

### Post by sn0m on 2010-02-12
dear experts
 I've written this script, with your help to have certain flv and wmv files converted to audio and mp4 for my nokia 5800.

This is the scripts:
#!/bin/bash
workingdirectory=/home/koli/dwhelper
cd $workingdirectory
#check for flv and do convert to mp3 as well as mp4 and move them to respective folders
 if [ -e *.flv ]; then
  for i in *.flv ; do ffmpeg -i "$i" -acodec copy "$i".mp3 > /dev/null 2>&1 ; done
   sleep 2s
  for i in *.flv ; do ffmpeg -i "$i" -f mp4 -vcodec libxvid -s 640x360 -b 768kb -r 25 -aspect 16:9 -acodec libfaac -ab 96kb -ar 44100 -ac 2 "$i".mp4 > /dev/null 2>&1 ; done
  sleep 3s
  mv *.mp3 /home/koli/Music/mp3_radio_files
   mv *.mp4 /home/koli/dwhelper/zonefornokia 
    mv *.flv /home/koli/dwhelper/videoforlaptop 
 else 
  exit
fi
#check for wmv and do convert to mp3 as well as mp4 and move them to respective folders
if [ -e *.wmv ]; then
  for i in *.wmv ; do ffmpeg -i "$i" -acodec copy "$i".mp3 > /dev/null 2>&1 ; done
  sleep 2s
 for i in *.wmv ; do ffmpeg -i "$i" -f mp4 -vcodec libxvid -s 640x360 -b 768kb -r 25 -aspect 16:9 -acodec libfaac -ab 96kb -ar 44100 -ac 2 "$i".mp4 > /dev/null 2>&1 ; done
 sleep 3s
 mv *.mp3 /home/koli/Music/mp3_radio_files
  mv *.mp4 /home/koli/dwhelper/zonefornokia 
   mv *.wmv /home/koli/dwhelper/videoforlaptop 
else
  exit
fi


now when i try to execute i get this:

koli@koli-laptop:~$ ./my_scripts/exp/convert.sh 
./my_scripts/exp/convert.sh: line 5: [: too many arguments
koli@koli-laptop:~$

I suspects this happens because there are more then 2 flv files in the folder.
Is there any option that bash checks whether a flv or wmv file is present in the folder and doesn't get hindered by the number of such files inside?
Reg
Sokol

---

### Post by diesch on 2010-02-12
*if [ -e *.flv ]; then *only works if there's exactly one file matching **.flv*, otherwise you get an error.

Use
*  if ls *.flv; then *
instead

---

