---
title: "help with mplayer script"
date: 2009-08-25
forum: General Help
---

### Post by sn0m on 2009-08-25
Hi guys
I have written a script which uses mplayer to download a few shows from my favorite online radio.
The problem is that some times this radio does not play online, but my script continues to run for an hour before exiting.
Is there a way to condition it: ie

if [ mplayer playback ok ]; then
 run script
else 
 echo "no playback"
fi
I'm not quite good with mplayer so any help is appreciated.
Thanks

Sokol

---

### Post by uylug on 2009-08-25
> **sn0m said:**
> Hi guys
I have written a script which uses mplayer to download a few shows from my favorite online radio.
The problem is that some times this radio does not play online, but my script continues to run for an hour before exiting.
Is there a way to condition it: ie

if [ mplayer playback ok ]; then
 run script
else 
 echo "no playback"
fi
I'm not quite good with mplayer so any help is appreciated.
Thanks

Sokol

Wow! I really have no idea how to solve your issue but I'm really interested in the scripts. How does it work?

---

### Post by sn0m on 2009-08-25
there have been quite a few how to in here. Following is my script, should you find it useful:

#!/bin/sh -x
#---------------------------------------------------------------------
# A very simple script to capture live stream from Top Albania Radio:
#---------------------------------------------------------------------
# Most of the variables:
DATE1=$(date +%d-%B)
DATE2=$(date +%Y)
DATE3=$(date +%R)
STREAM=http://tar.serverroom.us:9078/
DURATION=1h
DEST="38.96.148.64"
MUSIC_DIR=/home/koli/Music/temporary
BURN_DIR=/home/koli/Music/cd_radio_files
MP3_FILES=/home/koli/Music/mp3_radio_files
# For the id3v2 Tags
AUTHOR="Top Albania Radio"
ALBUM="morning_show"
TITLE="wake_up.$DATE1"
COMMENT="Wake up show"
#VAR=`ping -s 1 -c 1 $DEST > /dev/null; echo $?`
#if [ $VAR -eq 0 ]; then
cd $MUSIC_DIR
# Download the stream$S and convert it to wave format
#it needs to have -really-quiet option for cron to execute:
/usr/bin/mplayer -vc null -really-quiet -format s16le -vo null -ao pcm:fast:waveheader:file=wup.wav "$STREAM" &
/bin/sleep $DURATION # Length of the program being recorded as background. 
/bin/kill $!         # End the most recently backgrounded job = mplayer en
if [ wup.wav -e ]; then
  {   # Find the best volume adjustment and apply this to the wav file.
       /usr/bin/sox wup.wav -n stat > stats 2>&1 || exit 1
       VOL=$(grep 'Volume' stats | sed 's/^.*[ \t]//')
       /usr/bin/sox -v $VOL wup.wav wup$DATE1.wav || exit 1
       rm wup.wav
    # Convert to mp3
      /usr/bin/lame -S -h -t -V 6 wup$DATE1.wav wup.$DATE1.mp3 
    # remove old tags from the resulting captured .mp3
      /usr/bin/id3v2 -D wup.$DATE1.mp3
    #new tags: 
      /usr/bin/id3v2 -a "$AUTHOR" \
      -A "$ALBUM"  \
      -t "$TITLE"  \
      -y "$DATE2"  \
      -c "$COMMENT" \
      wup.$DATE1.mp3
   # Clean up:
     /bin/rm stats
   #mv wav file to wav directory
    /bin/mv -f wup$DATE1.wav $BURN_DIR
   #mv mp3 files to mp3 directory
     /bin/mv -f wup.$DATE1.mp3 $MP3_FILES
   #change direct for cd burner
     cd $BURN_DIR
   #change sample rating to cd sample using ch_wave
      /usr/bin/ch_wave -otype riff -F 44100 -o wup_cd.wav -pc FIRST wup$DATE1.wav wup$DATE1.wav
      /bin/rm wup$DATE1.wav
   #burn to cd using cdrecord yet not workimg from cron, wodim -scanbus or wodim --devices 
    #to find what cd record in kernel
      /usr/bin/cdrecord -s -pad speed=1 dev=1,0,0 -dao -audio -swab -force wup_cd.wav
   #clean old files
      /bin/rm wup_cd.wav
   #eject cd
   #/usr/bin/eject
 }
else
    echo "TAR not online"
fi


obviously I tried to do it via ping, but a successfull ping does not guarantee playback, therefore I want the script to exit if there's no playback. At the moment mplayer will carry on for an hour before stopping.
thanks
Sokol

---

