---
title: "Using sed to retrieve last played position of mp3 file in mplayer"
date: 2009-08-21
forum: General Help
---

### Post by wayfarer_boy on 2009-08-21
Hi everyone

I'm writing a sed command that will look through mplayer output and check to see if mplayer was stopped or skipped before it finished playing an mp3 file.

I'm trying to use sed to parse the line that has the last "A: seconds_played" info when mplayer was stopped.  Here's an example of the last 10 lines of the output file:
```
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 1 ch, s16le, 64.0 kbit/9.07% (ratio: 8000->88200)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 44100Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   5.8 (05.8) of -8.9 (unknown)  0.5% 91% 

MPlayer interrupted by signal 2 in module: play_audio
```
Here's the sed command I'm using that finds the line beginning with A: and retrieves the next number:
```
sed -n -e 's/^A:[^0-9]*\([0-9]\{1,\}\).*$/\1/p' /path/to/mplayer/output
```
What *should* be returned is **5**, but instead I get **0**.  Where am I going wrong?  I've stared at this one line for over an hour now!

Thanks for any help you can give me.

---

### Post by DaithiF on 2009-08-22
strange, works for me.  For you it seems to be matching the line 
```
A0: [pulse] 44100Hz 1ch s16le (2 bytes per sample)
```
what version of sed are you using? (sed --version).
I just wonder if its an older version that is interpreting the colon character as the beginning of a label rather than a character to match.  seems unlikely, but try escaping it as follows:
```
sed -n -e 's/^A\:[^0-9]*\([0-9]\{1,\}\).*$/\1/p' testfile
```

Actually, next thing I would do is expand the part of the line that you are capturing in parentheses to include everything to the end of the line, just so you get enough output to know for sure exactly which line you are matching against (in case there is more to the file than you listed here).

also, don't you want the fractional part of the time also? if so, include a . in the range you capture, like: [0-9.]

---

### Post by wayfarer_boy on 2009-08-22
Actually, you're right.  I tried the code I posted again, and it worked, returning the 5.  I'm not sure why that didn't work, but it was definitely returning a 0 at the time.  Ho hum.

Also, I've never considered sending a fraction to the mplayer -ss argument - I'm presuming it allows a fractional value?  I'll test it out to make sure :)

BTW, for anyone who's interested, here's an example of the current script:
```
#!/bin/bash

#~ A script to parse an rss feed, and play any files found within.
#~ It keeps a record of files played, and will replay files that are not on the list.
#~ It currently doesn`t cache the feed, so that`s my next job (not too difficult)
#~ and I'd also like it to remember the last position and play from there
#~ when the script is run again.

# This script is specific to my current setup - I have a google reader feed for spoken word podcasts
# and a feed for music podcasts, so once the podcasts are downloaded to a location on my home
# network by gPodder, my home feed checks the specified directory (along with any files downloaded
# from BBC iPlayer via get_iplayer) and creates a new rss feed for my N95 (and other gadgets) to pick up.

# This script is for my work machine to run when I'm working and just want the latest podcasts/iplayer
# recordings to play in the background.

#~ Wayfarer Boy, Aug 2009

# Work out whether the player is playing spoken word or music (any argument is considered music)
IP="10.0.0.11" # IP of the rss feed

if [[ $# -lt 1 ]]
then
    URL='http://$IP/podcasts/'
else
    URL='http://$IP/podcasts/?type=music'
fi

PREFIX='http://$IP/podcasts/' # Prefix for the location of the audio file
PLAYED='/home/$USER/scripts/podcasts-played' # Location of played list
OUTPUT='/home/$USER/scripts/podcasts-output' # Location of temporary mplayer output

# Make sure played and temp output files are there
touch $PLAYED
touch $OUTPUT
# Reset counter
COUNT=1

# Put something here about checking the cache or downloading the newer rss file

# Download podcast rss feed and parse for Artist, Album and Filename
# (removing spaces to make sure it loops correctly).
# This parsing is specific to the feed I'm subscribed to,
# so other feeds may be different in their layout
for FILE in `wget -q $URL -O - | \
            sed -n -e 's/.*<tr bgcolor="\#EEEEEE"><td align="left"><a href="\.\/\.\/\([^"]*\)">\([^<]*\)<\/a><\/td><td align="left"><a\([^>]*\)>\([^<]*\)<.*/\1~\2~\4/p' | \
            tr ' ' '|'`
do
    FILENAME=$PREFIX`echo "$FILE" | cut -d '~' -f 1`
    if [[ ! `grep "$FILENAME" "$PLAYED"` ]]
    then
        ARTIST=`echo "$FILE" | cut -d '~' -f 2 | tr '|' ' ' | sed -n -e 's/&nbsp;/ /g'`
        ALBUM=`echo "$FILE" | cut -d '~' -f 3 | tr '|' ' ' | sed -n -e 's/&nbsp;//g'`
        echo Playing $COUNT: $ARTIST - $ALBUM # Echo what is playing
        COUNT=$((COUNT+1))
        mplayer -cache-min 50 "$FILENAME" &> $OUTPUT # Play file
        # Find out if mplayer exited correctly (ie, finished the file or was skipped)
        # or if it was exited (CTRL-C or stream lost)
        EXIT=`tail $PLAYED -n 1`
        if [[ "$EXIT" == "Exiting... (End of file)" ]]
        then
            echo "$FILENAME" >> $PLAYED # Add filename to 'played' list
            rm $OUTPUT # Remove the mplayer output file
        else
            # Put something here about saving the last position
            exit 0 # Exit the loop and exit the script
        fi
    fi
done

exit 0

```

---

