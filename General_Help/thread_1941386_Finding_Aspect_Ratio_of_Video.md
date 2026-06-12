---
title: "Finding Aspect Ratio of Video"
date: 2012-03-15
forum: General Help
---

### Post by Kissell on 2012-03-15
I am able to find the aspect ratio of photos using imagemagick's identify program.  Is there something similar for videos?  

I am trying to find all the videos that are 4:3, and I have a lot of videos to do, but I can script the batch part...  I just want to do something like "command input.avi" and get returned "4:3" or "16:9" or at least the frame size in pixels then I can calculate it in a spreadsheet.

---

### Post by papibe on 2012-03-15
Hi Kissell.

The well-known program 'mediainfo' is available via ppa. [Here]("http://ubuntuforums.org/showthread.php?t=1941003&highlight=mediainfo")'s how to install it  (see post#2).

There are two versions. One of them is a command line tool.

This is the typical output of the command line version:
```
mediainfo Pioneer.One.S01E06.720p.x264-VODO.mkv

General
Unique ID                                : 72004449790908803125977288577907028330 (0x362B8D77126BAB543E2F5777E8E5F16A)
Complete name                            : Pioneer.One.S01E06.720p.x264-VODO.mkv
Format                                   : Matroska
Format version                           : Version 1
File size                                : 1.48 GiB
Duration                                 : 44mn 34s
Overall bit rate                         : 4 743 Kbps
Writing application                      : HandBrake 0.9.3

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : Main@L3.1
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 2 frames
Codec ID                                 : V_MPEG4/ISO/AVC
Duration                                 : 44mn 34s
Nominal bit rate                         : 5 000 Kbps
Width                                    : 1 280 pixels
Height                                   : 720 pixels
[SIZE="4"][COLOR="Red"]**Display aspect ratio                : 16:9**[/COLOR]
[/SIZE]Frame rate                               : 23.976 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.226
Writing library                          : x264 core 65
Encoding settings                        : cabac=1 / ref=2 / deblock=1:0:0 / analyse=0x1:0x111 / me=umh / subme=6 / psy_rd=1.0:0.0 / mixed_ref=0 / me_range=16 / chroma_me=1 / trellis=0 / 8x8dct=0 / cqm=0 / deadzone=21,11 / chroma_qp_offset=-2 / threads=12 / nr=0 / decimate=1 / mbaff=0 / bframes=2 / b_pyramid=0 / b_adapt=1 / b_bias=0 / direct=1 / wpredb=0 / keyint=240 / keyint_min=24 / scenecut=40(pre) / rc=abr / bitrate=5000 / ratetol=1.0 / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / ip_ratio=1.40 / pb_ratio=1.30 / aq=1:1.00
Language                                 : English
Color primaries                          : BT.709-5, BT.1361, IEC 61966-2-4, SMPTE RP177
Transfer characteristics                 : BT.709-5, BT.1361
Matrix coefficients                      : BT.709-5, BT.1361, IEC 61966-2-4 709, SMPTE RP177

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : A_AAC
Duration                                 : 44mn 34s
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Language                                 : English

```

As you can see, one of the information reported is the 'Display aspect ratio'. Then it would be just a matter of greping the output.

For example:
```
mediainfo Pioneer.One.S01E06.720p.x264-VODO.mkv | awk '/Display aspect ratio/{print $5}'

16:9

```
I hope that helps.
Regards.

---

### Post by Kissell on 2012-03-15
That's a great tool!

Should be able to quickly figure out which videos are 4:3 with this.

---

### Post by Kissell on 2012-03-15
Just thought I'd share the script I threw together to grab this information.  It assumes your movies are stored in folders and uses that for the movie name, as should be the case for using XBMC. 


```

#!/bin/bash 
#
# Aspect Ratio Lister by Kissell
# creates aspect-ratio-results.txt in $LOCATION

LOCATION="/path/to/files"
FILE_EXTENSION="avi"

if [ "$1" ]; then
  LOCATION="$1"
fi

if [ ! -s "/usr/bin/mediainfo" ]; then
  sudo add-apt-repository -y ppa:shiki/mediainfo
  sudo apt-get -y update
  sudo apt-get -y install mediainfo
fi

if [ -d "$LOCATION" ]; then
  FILES=`find "$LOCATION"  -maxdepth 2 -type f -name "*.$FILE_EXTENSION" |sort |sed 's: :_:g'`
  for NEXT_FILE in ${FILES[@]}; do
    NEXT_FILE=$(echo "$NEXT_FILE"|sed 's:_: :g')  
    FOLDER_NAME=${NEXT_FILE%/*}
    FOLDER_NAME=$(echo "$FOLDER_NAME"|sed s:$LOCATION/::g)
    ASPECT_RATIO=`/usr/bin/mediainfo "$NEXT_FILE" | awk '/Display aspect ratio/{print $5}'`
    echo "\"$FOLDER_NAME\",\"$ASPECT_RATIO\""
    echo "\"$FOLDER_NAME\",\"$ASPECT_RATIO\"" >> "$LOCATION"/aspect-ratio-results.txt
  done
else
  echo "Directory does not exist: $LOCATION"
fi

```

It'll create a spreadsheet file called aspect-ratio-results.txt that will look something like this, so you can then sort that or do whatever to find the relevant information about your movies.  This script can also be easily adapted to include additional fields of information from the mediainfo program.

> 
"300 (2006)","2.40:1"
"9 (2009)","1.875"
"A Beautiful Mind (2001)","1.400"
"Ace Ventura - Pet Detective (1994)","3:2"
"Ace Ventura - When Nature Calls (1995)","16:9"
"A Charlie Brown Christmas (1965)","3:2"
"A Charlie Brown Thanksgiving (1973)","1.375"
"A Garfield Christmas Special (1987)","4:3"
"Air Force One (1997)","3:2"
"Airplane! (1980)","16:9"
"A Knight's Tale (2001)","2.40:1"
"Aladdin (1992)","1.667"
"Alice in Wonderland (2010)","16:9"


---

