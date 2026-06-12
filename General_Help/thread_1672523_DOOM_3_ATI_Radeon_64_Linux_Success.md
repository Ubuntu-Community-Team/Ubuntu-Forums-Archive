---
title: "DOOM 3 ATI Radeon 64 Linux Success"
date: 2011-01-21
forum: General Help
---

### Post by cadcam on 2011-01-21
So, me and some friends have been working on getting doom3 to function on the 64 bit console with pumped up radeons (crossfire et al).  it was a horrible process, but i finally discovered what had to be done.  a number of people on the web point to a different driver directory in the launch script.  it takes a slight redirection with the radeon.  without pointing at the right directory on a 64 linux install, you will receive a vertex array memory error sign -1 and some business....  

below is script i am using.  the sound business at the end destroyed the lag.  I also did some stuff in the console to achieve my 1080 16:9 screen without stretched circles. 

Type these in the console (brought up by the "`" key for us noobs....) 
  r_customHeight "1080"
  r_customWidth "1920"
  r_mode "-1"
  r_aspectRatio "1"
  vid_restart

prefix seta to hold?

Change the "x" to "-1" for a custom screen setting.
if your screen aspect ratio is 16:9, change the "x" to "1".??
If your screen aspect ratio is 16:10 or 15:9, change the "x" to "2".??


```

#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/usr/local/games/doom3/"
export LIBGL_DRIVERS_DIR=/usr/lib32/fglrx/dri
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
exec ./doom.x86 +set s_alsa_pcm plughw:0 +set NumberOfSpeakers 2 "$@"

```I'm just putting this out there so someone won't have to dig like i did....

A.

---

