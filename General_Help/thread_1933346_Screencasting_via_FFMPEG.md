---
title: "Screencasting via FFMPEG"
date: 2012-02-29
forum: General Help
---

### Post by HiImTye on 2012-02-29
I just made two bash scripts for capturing my desktop to upload to YouTube and to live capture and broadcast on Justin.tv and thought I would share them with everyone.

note: to capture desktop sounds via PulseAudio, [install pavucontrol]("apt://pavucontrol") (if it is not already) then go to 'Recording' and then select 'Monitor of ' like the screenshot attached. you must do this while you are recording
[ATTACH]213466[/ATTACH]
note2: this may require codecs that do not come with the default install (and therefore requires [Medibuntu]("http://medibuntu.org/"))
Note3: You will need to replace <Stream Key> with your JustinTV [Stream Key]("http://en.justin.tv/broadcast/adv_other")
Note4: Remember to give each of these permissions (from 'Properties' when you right click on them, like the screenshot attached)
[ATTACH]213467[/ATTACH]
Note5: Depending on your version of ffmpeg you may need to change '-vpre' to '-vpreset'
Note6: Remember to run these in a terminal (as pictured):
[ATTACH]213731[/ATTACH]
or else you will need to either terminate ffmpeg (YouTube.sh):
[ATTACH]213733[/ATTACH]
(not YouTube.sh or it will not combine/convert)
or JustinTV.sh and then ffmpeg:
[ATTACH]213732[/ATTACH]
 (as it runs an endless loop of captures for in case something goes wrong with the connection). it's easier to just run them in a terminal and you can just ctrl+c ffmpeg (or hit 'q' depending on your version of ffmpeg)
(pictured is [HTOP]("apt://htop"), an ncurses process monitor, running inside [Guake]("apt://guake"), a Quake style drop down terminal)

JustinTV.sh
```
#!/bin/bash
# *** Variables
 TEXT="Resolution"
 OPTION1="1920x1080"
 OPTION2="1360x768"
 DIMENSIONS="$(zenity --list --radiolist --text $TEXT --column "" --column "Choose" TRUE $OPTION1 FALSE $OPTION2 FALSE "Other")"
 if [ "$DIMENSIONS" = "Other" ]; then
   DIMENSIONS=$(zenity --entry --text $TEXT)
 elif [ "$DIMENSIONS" = "" ]; then
   clear
   echo Cancelled By User Input at: $TEXT
   sleep 1
   exit
 fi
 echo $TEXT=$DIMENSIONS
 TEXT="Audiosink"
 OPTION1="pulse"
 OPTION2="hw:0,0"
 AUDIOSINK="$(zenity --list --radiolist --text $TEXT --column "" --column "Choose" TRUE $OPTION1 FALSE $OPTION2 FALSE "Other")"
 if [ "$AUDIOSINK" = "Other" ]; then
   AUDIOSINK=$(zenity --entry --text $TEXT)
 elif [ "$AUDIOSINK" = "" ]; then
   clear
   echo Cancelled By User Input at: $TEXT
   sleep 1
   exit
 fi
 echo $TEXT=$AUDIOSINK
 TEXT="Framerate"
 FRAMERATE=$(zenity --scale --text $TEXT --min-value=1 --max-value=30 --value=15 --step 2)
 if [ "$FRAMERATE" = "" ]; then
   clear
   echo Cancelled By User Input at: $TEXT
   sleep 1
   exit
 else
   echo $TEXT=$FRAMERATE
 fi

# *** Meat 'n Pooptatoes
 while :
 do
   sleep 15
   if ! ps -e | grep ffmpeg; then
     ffmpeg -f x11grab -s $DIMENSIONS -r $FRAMERATE -i $DISPLAY -f alsa -i $AUDIOSINK -acodec libmp3lame -ar 44100 -ac 1 -ab 48000 -vcodec libx264 -vpre "fast" -b 450000 -r $FRAMERATE -vsync 2 -s 640x360 -aspect 16:9 -f flv "rtmp://live.justin.tv/app/<Stream Key>"
   fi
 done

sleep 1
exit
```YouTube.sh
```
#!/bin/bash

# put your videos folder here. it's usually $HOME/Videos but if you use a
 # different one, you can change it
basevideosfolder="$HOME/Videos"
# the video preset we are going to use for capture. different presets will give captures of different quality
videopreset="lossless_ultrafast"

# the folder we're going to use
videosfolder="$basevideosfolder/YouTube"
if [ ! -d "$videosfolder" ]; then
 mkdir $videosfolder
fi

# the base name of our capture files
capturefile=$videosfolder/.capture

# Start Log
rm -f $capturefile.mkv $capturefile.wav $capturefile.log ffmpeg2pass*.log
echo Start of Process > $capturefile.log

# Variables
TEXT="Resolution"
OPTION1="$(xrandr --current|sed -n 's/.*current[ ]\([0-9]*\) x \([0-9]*\),.*/\1x\2/p')"
DIMENSIONS="$(zenity --list --radiolist --text $TEXT --column "" --column "Choose" TRUE $OPTION1 FALSE "Other")"
if [ "$DIMENSIONS" = "Other" ]; then
 DIMENSIONS=$(zenity --entry --text $TEXT)
elif [ "$DIMENSIONS" = "" ]; then
 clear
 echo Cancelled By User Input at: $TEXT >> $capturefile.log
 sleep 1
 exit
fi
echo $TEXT=$DIMENSIONS >> $capturefile.log
TEXT="Audiosink"
OPTION1="pulse"
OPTION2="hw:0,0"
AUDIOSINK="$(zenity --list --radiolist --text $TEXT --column "" --column "Choose" TRUE $OPTION1 FALSE $OPTION2 FALSE "Other")"
if [ "$AUDIOSINK" = "Other" ]; then
 AUDIOSINK=$(zenity --entry --text $TEXT)
elif [ "$AUDIOSINK" = "" ]; then
 clear
 echo Cancelled By User Input at: $TEXT >> $capturefile.log
 sleep 1
 exit
fi
echo $TEXT=$AUDIOSINK >> $capturefile.log
TEXT="Framerate"
FRAMERATE=$(zenity --scale --text $TEXT --min-value=1 --max-value=30 --value=15 --step 2)
if [ "$FRAMERATE" = "" ]; then
 clear
 echo Cancelled By User Input at: $TEXT >> $capturefile.log
 sleep 1
 exit
else
 echo $TEXT=$FRAMERATE >> $capturefile.log
fi

# Capture
echo Capture >> $capturefile.log
ffmpeg -f alsa -ac 2 -i $AUDIOSINK -f x11grab -r $FRAMERATE -s $DIMENSIONS -i $DISPLAY -vcodec libx264 -vpre $videopreset -crf 0 -threads 0 $capturefile.mkv -acodec pcm_s16le $capturefile.wav
echo Status = $? >> $capturefile.log
if ! zenity --question --text="keep?"; then
 echo Cancelled, Removing Files
 rm -f $capturefile.wav $capturefile.mkv $capturefile.log ffmpeg2pass*.log
 exit
fi
# Filename
tempfilename=$(zenity --entry --text "What should we call the file?" --entry-text "YouTube")
# strip the .webm extension from it, if it exists
if echo "$tempfilename" | grep .webm; then
 eval tempfilename='$(echo "$tempfilename" | sed "s|.webm||")'
fi
# Offer to change the name of our video if our name is already used
if [ -f "$videosfolder/"$tempfilename".webm" ]; then
 echo duplicate file found, prompting user >> $capturefile.log
 dupefilename="$tempfilename"
 dupereference="$tempfilename"
 while :
 do
   # see if we have a number at the end of our filename like so: filename.number
   if echo "$dupefilename" | grep -E '\.[0-9]+$'; then
     # if so, make it our new count
     count=$(echo "$dupefilename" | sed 's|.*\.\([0-9]*\)$|\1|')
     eval dupefilename=$(echo "$dupefilename" | sed 's|\(.*\)\.[0-9]*$|\1|')
   else
     # if not, create it
     count=0
   fi
   # add 1 to our number
   count=$(expr $count + 1)
   # ask the user what to rename our video to
   dupefilename=$(zenity --entry --text "Duplicate exists, what should we call our new one?\nnote: cancel deletes the old file." --entry-text '"$dupefilename".$count')
   # strip the .webm extension from it, if it exists
   if echo "$dupefilename" | grep .webm; then
     eval dupefilename='$(echo "$dupefilename" | sed "s|.webm||")'
   fi
   #if our new filename is different than our old one, reset our count
   if [ ! "$dupefilename" = "$dupereference" ]; then
     count=0
   fi
   # exit the loop if we're not renaming the file
   if [ "$dupefilename" = "" ]; then
     break
   # exit the loop if the file doesn't exist
   elif [ ! -f "$videosfolder/"$dupefilename".webm" ]; then
     break
   fi
   dupereference="$dupefilename"
 done
 if [ "$dupefilename" = "" ]; then
   echo "deleting old file" >> $capturefile.log
   rm -f $videosfolder/"$tempfilename".webm
 else
   # fix our file name
   echo "our new file name" >> $capturefile.log
   # change our filename
   tempfilename="$dupefilename"
 fi
fi
# add our videos folder to our filename, to make it cleaner
filename=$videosfolder/."$tempfilename"
shownfilename=$videosfolder/"$tempfilename"
# Remove any old temporary files, to be sure
echo removing existing temp files starting with ."$tempfilename" >> $capturefile.log
rm -f "$filename".log "$filename".mkv "$filename".temp.mkv "$filename".wav
# Rename to allow a simultaneous capture while we convert
echo renaming current temp files >> $capturefile.log
mv -v $capturefile.mkv "$filename".mkv >> $capturefile.log
mv -v $capturefile.wav "$filename".wav >> $capturefile.log
# we have to echo here as the output isn't redirected after it's moved so the
 # move just overwrites the output
mv $capturefile.log "$filename".log ; echo "Log file renamed:" >> "$filename".log; echo "'$capturefile.log' -> '"$filename".log'" >> "$filename".log
# Combine
echo Combine >> "$filename".log
ffmpeg -i "$filename".mkv -i "$filename".wav -vcodec copy -acodec copy "$filename".temp.mkv
echo Status = $? >> "$filename".log
# Conversion
echo Conversion Pass 1 >> "$filename".log
ffmpeg -i "$filename".temp.mkv -an -vcodec libvpx -b 1000k -pass 1 "$shownfilename".webm
echo Status = $? >> "$filename".log
echo Conversion Pass 2 >> "$filename".log
ffmpeg -i "$filename".temp.mkv -acodec libvorbis -ab 128k -ac 2 -vcodec libvpx -b 1000k -pass 2 -y "$shownfilename".webm
echo Status = $? >> "$filename".log

echo Finished
echo End of Process >> "$filename".log
# Finalization
if zenity --question --text="clean up?"; then
 echo Removing Temporary Files
 rm -f "$filename".mkv "$filename".temp.mkv "$filename".wav "$filename".log ffmpeg2pass*.log
else
 echo Skipped Removal of Temp Files
fi

sleep 1
exit
```


Updates
-automagically grab the size of the display and make it the only option other than 'other' for a custom size
-change $0.0 to $DISPLAY so we don't have to get it every time
-added move/rename and configurable video folder to YouTube.sh
-changed YouTube.sh to move/rename when it's done capturing, to allow for a second capture while it converts as well as to offer to replace an existing video with the same filename, among other things
-added better handling of existing files to YouTube.sh
-fixed YouTube.sh's handling of filenames with spaces
-YouTube.sh: easily configurable video preset and changed the preset to 'lossless_ultrafast'

---

### Post by dannyboy79 on 2012-12-01
when trying this I get
Could not open 'rtmp://live.justin.tv/app/MYLIVEKEYHERE'

Do you know why it's failing?

---

