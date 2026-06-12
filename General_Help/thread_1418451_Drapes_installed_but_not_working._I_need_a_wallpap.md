---
title: "Drapes installed but not working. I need a wallpaper changer"
date: 2010-02-28
forum: General Help
---

### Post by joselitux on 2010-02-28
Hi all

I want to change my wallpaper on a timed basis. I've installed Desktop Drapes via Synaptics (in Karmic) but I'm not able to add to panel. However when I shut down my pc, an error dialog informs that Drapes is Running (4 or 5 instances) and asking if I really want to quit.

I've tested Wally, Wallpaper-Tray and Webilder. This three distort my images and show pixelated wallpapers.

Wallpapoz and Xml slideshow Creator seems to work but when I add more than 100 pictures they got freezed on a blank screen.

any help will ne appreciated

---

### Post by dcstar on 2010-02-28
> **joselitux said:**
> Hi all

I want to change my wallpaper on a timed basis. I've installed Desktop Drapes via Synaptics (in Karmic) but I'm not able to add to panel. However when I shut down my pc, an error dialog informs that Drapes is Running (4 or 5 instances) and asking if I really want to quit.

I've tested Wally, Wallpaper-Tray and Webilder. This three distort my images and show pixelated wallpapers.

Wallpapoz and Xml slideshow Creator seems to work but when I add more than 100 pictures they got freezed on a blank screen.

any help will ne appreciated

I use this script to update my wallpaper every few minutes with the xplanet app, you should be able to adapt it:

```
#!/bin/bash
#xplanet-gnome.sh shell script v0.3
#shows Earth on your Gnome desktop with current lighting conditions,i.e. day and night

DELAY=5m
PREFIX=~/
OUTPUT=.xplanet.png
#
# Change these to match your screen settings and your particular location
# One day someone might want to replace these with commands to automatically
# get them from your generic Linux system (but not today...)
#
GEOMETRY=1680x1050
LONGITUDE=144.833328
LATITUDE=37.666668
#
#default is no projection,i.e. render a globe
#rectangular is the flat world map. also try ancient, azimuthal,  mercator,..
PROJECTION=rectangular

# This stuff is to prevent multiple instances running if you log out and log in again
lockfile=$HOME/.xplanet.lock

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

#update Gnome backgound - this works in Ubuntu 9.04
gconftool -t str -s /desktop/gnome/background/picture_filename "$PREFIX$OUTPUT"
sleep $DELAY
rm $lockfile
exec $0
```

---

### Post by 2hot6ft2 on 2010-02-28
Here's one I've used and it worked great
Applications > Accessories > Terminal
```
sudo apt-get install wallpaper-tray
```
Or search for it in Synaptic
System > Administration > Synaptic Package Manager

---

### Post by joselitux on 2010-03-01
> **joselitux said:**
> 
I've tested Wally, Wallpaper-Tray and Webilder. This three distort my images and show pixelated wallpapers. 

Wallpaper-tray distort the images

---

### Post by joselitux on 2010-03-01
dcstar, what is supposed to do with that piece of code?

---

### Post by joeknoodle on 2010-03-01
> **joselitux said:**
> Wallpaper-tray distort the images
Try settings in wp-tray...

WP-tray Icon > Preferences > More Options > Picture Options

There you have...

Stretched: Scales small images to fit screen <likely your distortion is this one

Scaled: fits entire picture into the desktop (resize big pics)

Wallpaper: Keep image size (big pics go off screen)

Centered: Not sure, but big pics still go off screen

---

