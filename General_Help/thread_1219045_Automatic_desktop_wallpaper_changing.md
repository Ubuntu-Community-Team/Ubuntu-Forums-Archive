---
title: "Automatic desktop wallpaper changing?"
date: 2009-07-21
forum: General Help
---

### Post by H.K.Murmu on 2009-07-21
Dear friends,
Is there any method/application to change desktop wallpaper automatic in a time interval or every login?
If there is, you are welcome,share it.

---

### Post by Keith Hedger on 2009-07-21
I used to run this script at login to set a random wallpaper, I'm sure you could alter it to pick a new wallpaper every so often.```
#!/bin/bash

sleep 1

PICDIR=/media/LinuxData/XMasWallpapers
PICNAMES=( $(find -L $PICDIR | grep -i jpg) )
NUMBER=$RANDOM
MAXFILES=${#PICNAMES[@]}
PIC=${PICNAMES[ $(( NUMBER %=  MAXFILES ))]}

gconftool-2 --type string --set /desktop/gnome/background/picture_filename $PIC
```
Obviously you would have to change the line that sets the folder that holds the pics to suit your self

---

### Post by tjeremiah on 2009-07-21
Go to System > Administration > Synaptic Package Manager  > Type in  ```
wallpaper-tray 
``` > Download > Once installed, right click on panel > select Add to Panel > Add Wallpaper Tray.

---

### Post by mano cazalet on 2009-07-21
sudo apt-get install wallpaper-tray

---

### Post by CatKiller on 2009-07-21
I've got a similar one, but in Python.

```

#!/usr/bin/env python

BACKGROUND_DIRS = ['/usr/share/backgrounds', '~/backgrounds']
EXTENSIONS = ['jpeg', 'jpg', 'bmp', 'png', 'svg']

import os, glob, random, itertools, gconf

files = list(itertools.chain(*[[os.path.join(dirpath, name)
                                for name in filenames]
                               for dirpath, dirnames, filenames in
                               itertools.chain(*[os.walk(os.path.expanduser(d))
                                                 for d in BACKGROUND_DIRS])]))
gconf.client_get_default().set_string(
    '/desktop/gnome/background/picture_filename',
    random.choice(files)) 

```

You can either just set your Startup Applications to run the script when you logon, or set a cron job to run the script every hour, say. Or both.

---

### Post by tjeremiah on 2009-07-21
> **mano cazalet said:**
> sudo apt-get install wallpaper-tray

yea,the more simple way..

---

### Post by rykel on 2010-08-16
$ sudo apt-get install wallpaper-tray
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wallpaper-tray

Any clue??

---

### Post by CatKiller on 2010-08-17
*wallpaper-tray* is included in the Universe repository up till Karmic. It isn't included in Lucid.

---

### Post by sgosnell on 2010-08-17
I use [wallpapoz](http://wallpapoz.akbarhome.com).

---

### Post by gerymate on 2010-08-18
There is an interesting one in the default install: the Cosmos background, which changes itself automatically... You may find it in the cosmos directory in /usr/share/backgrounds/ ...

---

### Post by clhsharky on 2010-08-18
I use CREBS, its has a gui and ppa
[http://www.omgubuntu.co.uk/2010/07/crebs-slideshow-generator-gets-new.html](http://www.omgubuntu.co.uk/2010/07/crebs-slideshow-generator-gets-new.html)

Sharky

---

### Post by corbcox on 2010-08-18
I've been using Desktop Drapes, is in Synaptic under Drapes.  Works great!

---

### Post by bark50 on 2010-08-18
Another option is Wally which can be found through Synaptic.  Besides accessing your pc for wallpapers, it will also pull from Flickr, Yahoo photos, and other sources if you want.

---

### Post by trikster_x on 2010-09-01
I use a bash script similar to one of the other posters:

```
#! /bin/bash
while :
 do
   files=(/usr/share/backgrounds/*/*.jpg)        # create an array of the files in a given directory.  Wild cards can be used here to look for files in subdirectories of any given directory.
   N=${#files[@]}          # Number of members in the array
   ((N=RANDOM%N))
   randomfile=${files[$N]}



   gconftool-2 --type string --set /desktop/gnome/background/picture_filename $randomfile  # set the file to use as a background and update background

   sleep 10 # chooses the next image every 10 seconds.  Simply change the number to change duration.
 done
```

The only drawback for me is that all the backgrounds that are cycled through end up in your appearances menu, resulting in a bit of a mess after a while.  

I prefer to do as much with scripts and bash commands as I can because it offers a bit more security when you live in a house where a few people have access to the computer and like to see how long it takes for you to fix the software they broke, or settings they changed.

---

### Post by rykel on 2010-09-01
I am using Lucid and I found that Desktop Drapes works. However, despite "enable Desktop Drapes at Startup" and having Desktop Drapes in the list of Startup Applications, the program does NOT start itself upon a new login. Please help?

---

### Post by inameiname on 2010-09-01
Here's the script I use. You can set it to run at timed intervals if you'd like:

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

```

---

### Post by Noobie` on 2011-05-07
@inameiname wow, great script. Thanks a lot. is there any way you can make it run on startup and in the background i.e that you can close the terminal and it keeps runnning?

I always used DesktopNova to do this, but since Unity (11.04) DesktopNova doesnt work anymore. else if you know how to get it working or another app please tell me bout it.

thanks in advance!


aka Punisher`

:)

---

### Post by inameiname on 2011-05-07
Yep, it is very easy. No need for any wallpaper/background changing software. Here is how I do it:

```

To add to the Startup Applications (adds to the notification and/or runs at startup)

Go to System > Preferences > Startup Applications

Name: Random Wallpaper
Command: /usr/bin/python /home/(your username)/.gnome2/nautilus-scripts/Random-Wallpaper.py
Comment: Changes desktop background at startup

...and make sure you have that startup application checked

```Also, since I last posted, I found another script that works better for me. When run, it checks two folders (more if you'd like): '/usr/share/backgrounds' and '~/Pictures/Backgrounds'. As such, I keep 300+ pictures inside my '~/Pictures/Backgrounds' folder and at every start up, it changes backgrounds. Why I chose this script instead of the other is I do not really need one to run every N seconds, but at every start up, and this is simple, does not continuously run like the other, and just works and turns off. However, if a random change of the background every N seconds is what you want, just replace the first script instead of the one below, and you will have what you want.

```

#!/usr/bin/env python

BACKGROUND_DIRS = ['/usr/share/backgrounds', '~/Pictures/Backgrounds']
EXTENSIONS = ['jpeg', 'jpg', 'bmp', 'png', 'svg']

import os, glob, random, itertools, gconf

files = list(itertools.chain(*[[os.path.join(dirpath, name)
                                for name in filenames]
                               for dirpath, dirnames, filenames in
                               itertools.chain(*[os.walk(os.path.expanduser(d))
                                                 for d in BACKGROUND_DIRS])]))
gconf.client_get_default().set_string(
    '/desktop/gnome/background/picture_filename',
    random.choice(files))

```Actually, if you do indeed prefer a random wallpaper changer every N seconds and desire an actual program, not just setting up a script to run at start up, (and not how I prefer which is once every restart), I would check out CreBS Wallpaper changer. It is easy to use, and integrates well into an Ubuntu desktop.

[http://www.omgubuntu.co.uk/2010/06/crebs-wallpaper-slideshow-generator-gets-a-ppa-new-features/](http://www.omgubuntu.co.uk/2010/06/crebs-wallpaper-slideshow-generator-gets-a-ppa-new-features/)

---

### Post by stevedude on 2011-05-07
I use "Wally" it is in the Ubuntu Software Center described as a KDE4 Wallpaper Changer.

With Wally you can choose from several locations like Picasa, PhotoBucket, etc, and from your own local directory. You can set the change interval from minutes, to days, weeks, months and to change every time you log in.

Some of the user photographs and art that Wally finds are astounding, some are just plain bad. You are able to search what you want to use on your desktop by setting "tags".

If you don't like what Wally has served up, just right-click and choose "Next".

** You will have to edit the system tray in Natty to allow Wally to reside there, and you will have to create a startup program launcher. Editing the system tray is listed under Known Bugs in this General forum and on the webupd8 website.

---

### Post by inameiname on 2011-05-08
Thanks for mentioning Wally, stevedude. I forgot about it. It is definitely another option.

Personally, it is a bit too much for me, but I know it is quite popular. And it kept giving me issues, and from what I can recall, I think Google Images is not one of the search engines used, which would be good. 

Regardless, definitely an option.

---

