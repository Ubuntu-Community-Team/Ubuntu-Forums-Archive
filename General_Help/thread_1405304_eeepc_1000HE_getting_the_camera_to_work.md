---
title: "eeepc 1000HE getting the camera to work"
date: 2010-02-12
forum: General Help
---

### Post by jeff.sadowski on 2010-02-12
The instructions I found on the net were helpful but I never saw a real solution that really worked.

I setup my eeepc with a few scripts to take video and snapshots.

I figured out why snapshot software wasn't working; because the camera needs time to warm up.

cheese works pretty good for snapshots; however I wanted a script to take a snapshot that could be run via xbindkeys

of course the camera needs to be enabled

sudo cat /sys/devices/platform/eeepc/camera
if its not 1
do
echo 1 > /sys/devices/platform/eeepc/camera

I found this on many sites

I found some helpful mencoder examples similar to mine here is my script to start and stop a capture

> #!/bin/bash
#
# toggle_record.sh
#
if [ -f ~/.recording_pid ]; then
 kill `cat ~/.recording_pid`
 rm ~/.recording_pid
else
 mencoder tv:// -tv \
 driver=v4l2:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp \
 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 \
 -o ~/Videos/webcam-`date "+%F-%H:%M:%S"`.avi &
 ps| grep mencoder | awk '{print $1}' > ~/.recording_pid
fi


After struggling to get a picture for a while I figured out what was going on by watching the videos I was recording.
I noticed that the videos started really dark and that ten frames in it got much clearer. That discovery led me to the following script to get a picture.

> #!/bin/bash
#
# snap.sh
#
file=/tmp/webcam-`date "+%F-%H:%M:%S"`.avi
mencoder tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0 \
-ovc lavc -frames 15 -o ${file} 2>/dev/null >/dev/null
dir=`mktemp -d`
mplayer -vo jpeg:outdir="$dir" $file 2>/dev/null >/dev/null
last=`ls -1 $dir | tail -n 1`
mv $dir/$last ~/Pictures/webcam-`date "+%F-%H:%M:%S"`.jpg
rm -rf $file $dir


then I used xbinkeys using this good tutorial
[http://ubuntuforums.org/showthread.php?t=79560&page=1](http://ubuntuforums.org/showthread.php?t=79560&page=1)
I had to move the xbindkeys-config around using alt+[mouse drag]

clicked on new
Named it "Video Capture"
clicked on "Get Key" and I wanted the right button that looks like a photo to run my capture script and the left one to run my snapshot script
so I put the path to it in the command and hit save and apply and wala
When I hit the right picture button it starts recording
Hit it again it stops When I hit the the left button it takes a snapshot

Later I will writeup my screen resize commands you can display a larger resolution without scrolling than your monitor can support.

I have a script that changes the resolution to 1920x1080

---

