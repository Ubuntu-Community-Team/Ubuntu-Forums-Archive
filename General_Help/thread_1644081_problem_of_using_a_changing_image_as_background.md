---
title: "problem of using a changing image as background"
date: 2010-12-12
forum: General Help
---

### Post by cnbiz850 on 2010-12-12
I have been using the earth image as desktop's background.  The image is updated every hour from the web.  However, after I upgraded to Maverick, the background is most often incomplete.  Basically, the bottom part (large or small at different time) is missing.  The image itself is fine though.  What I have to do to correct the background is to change to another image then change back manually.  Initially, it is fine, but later-on (I guess when the image gets updated) the problem occurs again.

Anyone know what might be the problem?

---

### Post by dcstar on 2010-12-13
> **cnbiz850 said:**
> I have been using the earth image as desktop's background.  The image is updated every hour from the web.  However, after I upgraded to Maverick, the background is most often incomplete.  Basically, the bottom part (large or small at different time) is missing.  The image itself is fine though.  What I have to do to correct the background is to change to another image then change back manually.  Initially, it is fine, but later-on (I guess when the image gets updated) the problem occurs again.

Anyone know what might be the problem?

Video drivers can cause this sort of problem. This is the script I use in 10.04 to update my background, the part that is relevant to you is at the bottom:

```
#!/bin/bash
#xplanet-gnome.sh shell script v1.1
#shows Earth on your Gnome desktop with current lighting conditions,i.e. day and night

DELAY=5m
PREFIX=~/
OUTPUT=.xplanet.png
#
# These should extract your current screen resolution and location from your system
# The location is found from the Gnome Clock Preferences Location.
#
GEOMETRY=$(xrandr | grep '*' | head -1 | cut -b 4-12)
LONGITUDE=$(gconftool -g /apps/panel/applets/clock_screen0/prefs/cities | cut -f5 -d " " | cut -f2 -d "=" | sed 's/"//g' )
LATITUDE=$(gconftool -g /apps/panel/applets/clock_screen0/prefs/cities | cut -f4 -d " " | cut -f2 -d "=" | sed 's/"//g' )
#
#default is no projection,i.e. render a globe
#rectangular is the flat world map. also try ancient, azimuthal,  mercator,..
PROJECTION=rectangular

# This stuff is to prevent multiple instances running if you log out and log in again
lockfile=$HOME/.xplanet.lock

# Check if timestamp of lock file is older than boot time:
if [ -e $lockfile ]; then
  CDATE=$(date +%s -r $HOME/.xplanet.lock)
  BOOTTIME=$(cat /proc/uptime | cut -f1 -d" ")
  CTIME=$(date +%s)
  FTIME=$(($CTIME - ${BOOTTIME/.*}))
  #
  # If older then it is a leftover - so delete it!
  if [[ $CDATE -lt $FTIME ]]; then
   rm -f $lockfile
 fi
#
fi

if [ ! -e $lockfile ]; then
   # Delete lockfile if program receives command to end:
   trap "rm -f $lockfile; rm -f $PREFIX$OUTPUT; exit" INT TERM EXIT
   # and let's make one now....
   touch $lockfile
else
   # Lockfile exists for this user profile, get me outa here!
   exit
fi

if [ -z $PROJECTION ]; then 
xplanet -num_times 1 -output "$PREFIX$OUTPUT" -geometry $GEOMETRY -longitude $LONGITUDE -latitude $LATITUDE
else
xplanet -num_times 1 -output "$PREFIX$OUTPUT" -geometry $GEOMETRY -longitude $LONGITUDE -latitude $LATITUDE -projection $PROJECTION
fi

#update Gnome backgound - this works in Ubuntu 9.04 & 10.04
gconftool -t str -s /desktop/gnome/background/picture_filename "$PREFIX$OUTPUT"
sleep $DELAY
rm $lockfile
exec $0

```

---

### Post by cnbiz850 on 2010-12-14
Thanks very much for the reply.  

I don't understand why it can be video drivers' problem.  I didn't have it running Karmic.  Is Maverick's driver somehow different from Karmic's?  Here is the output from lshw: 
```
           *-display
                description: VGA compatible controller
                product: M92 [Mobility Radeon HD 4500 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:49 memory:d0000000-dfffffff ioport:2000(size=256) memory:fc000000-fc00ffff memory:fc020000-fc03ffff 
```

The gconftool conmand does reset it.  I created a script based on yours and make the wallpaper reset every half an hour.  Will see the result.  Thanks again for the help.

---

### Post by cnbiz850 on 2010-12-14
Well actually, the gconftool conmand doesn't redraw the wallpaper.  How to redraw it?

---

