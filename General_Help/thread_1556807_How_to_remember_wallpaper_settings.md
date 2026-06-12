---
title: "How to remember wallpaper settings?"
date: 2010-08-19
forum: General Help
---

### Post by dosfool on 2010-08-19
Hello everyone, long time reader fist time poster. I cane never decide on a single wallpaper so I managed to put together this little script, mostly by stealing from other people, and have it run on start up:

#!/bin/bash
cd "/home/max/Pictures/wallpapers"
set -- *
length=$#
file="${@:RANDOM%($#+1):1}"
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/max/Pictures/wallpapers/"$file

Now I have 2 problems: The first and most important is that my computer doesn't remember the settings for each picture, it just uses whatever the previous settings were. Is there a way to fix this? and the second very minor problem is that sometimes the script uses no picture so I just have whatever backround color was set as the wallpaper.

- thanks for your time, hope this is helpful to someone else as well

---

### Post by inameiname on 2010-08-20
I'm the same and found a really good script that I run at every startup which changes my background automatically to whatever is in my /home/(my username)/Pictures/Backgrounds folder. Maybe it'll work well for you as well:

```

#!/usr/bin/env python

import subprocess
import os
import sys
import time
import random

# The default wallpaper interval (pass -t seconds to override)
changetime = 1800.0
# The default wallpaper folder (must have only Gnome supported images)
imagefolder = "~/Pictures/Backgrounds/"
# The pictures in "/usr/share/backgrounds/" are linked into the above

lastpicindex = 0

def get_pictures (folder):
    try:
        pictures = os.listdir (folder)
        return pictures

    except OSError:
        print "Folder " + folder + " not found."
        sys.exit ()

def change_curscreen (folder, pictures, type):
    # learn to use python :)
    if "random" != type:
        return 0

    picindex = lastpicindex
    while picindex == lastpicindex:
        picindex = random.randint (0, len (pictures) - 1)
    
    curpicture = pictures [picindex]
    
    command = 'gconftool-2 --set /desktop/gnome/background/picture_filename --type string "' + folder + curpicture + '"'
    subprocess.Popen (command, shell=True)

    print "changing screen to " + folder + curpicture
    time.sleep (changetime)

def start_screenchanger (folder):
    global changetime

    pictures = get_pictures (folder)
    change_curscreen (folder, pictures, "random");

def filter_foldername (folder):
    if not folder.endswith ('/'):
        folder += '/'

    command = "echo " + folder
    try:
        unixfilter = subprocess.Popen (command, stdout=subprocess.PIPE, shell=True)
        folder = unixfilter.communicate ()

    except OSError:    
        print folder
        print "Failed to launch unix echo command"
        sys.exit ()

    retfolder = folder[0].strip ('\n')
    return retfolder

def display_help ():
    print ""
    print "Simple background changer script 0.1"
    print "\t--help or -h\t\t\tDisplay this help message"
    print "\t--time or -t <seconds>\t\tWallpaper change interval in seconds"
    print ""

def main ():
    global changetime
    global imagefolder

    for i in xrange (0, len (sys.argv)):
        if sys.argv [i] == "--time" or sys.argv [i] == "-t":
            changetime = float (sys.argv [i + 1])
        elif sys.argv [i] == "-h" or sys.argv [i] == "--help" or sys.argv [i] == "-help":
            display_help ()
            sys.exit ()

    imagefolder = filter_foldername (imagefolder)

    while (1):
        start_screenchanger (imagefolder)

main ()

```To add 'Random Wallpaper' to the Startup Applications:

Go to System > Preferences > Startup Applications

'Add' it using the following parameters (or something similar):

Name: Random Wallpaper
Command: /usr/bin/python /home/me/.gnome2/nautilus-scripts/My_Scripts/Random-Wallpaper/Random-Wallpaper.py
Comment: Changes desktop background at startup

If you wish, you can also change the duration a little and it'll change backgrounds at a designated interval. Oh, and another great application if that more suits your needs is too:

[http://www.obfuscatepenguin.net/crebs/](http://www.obfuscatepenguin.net/crebs/)

---

### Post by dosfool on 2010-08-29
Sorry took so long to get back to you, I checked out that python script, but it's got the same problem. I need to find some way for the computer to remember the background settings for each image, so that when a new image is chosen I can go into change background and edit the background color and weather the image should be spanned, zoomed, centered etc and the next time that image is chosen the computer will set those same settings again.

---

### Post by inameiname on 2010-08-29
Hmmm, we I've never had a problem with it messing up the display of any picture I put inside my designated folder. It's always on stretch, which works for me. I keep 200 lovely nature/cityscape wallpapers I got from online and they always show up wonderful.

Uhm, then perhaps you should try that CreBS. It's growing really popular in the past few months and works well. It might size them up just fine for you whereas neither or those scripts work for you.

---

