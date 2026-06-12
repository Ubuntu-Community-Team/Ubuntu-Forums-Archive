---
title: "Scripts, feh, Xfce. Beginner"
date: 2009-11-26
forum: General Help
---

### Post by embryo_ on 2009-11-26
Hi!

I have installed Xubuntu on an old laptop. Have no experience with Linux, but with a bit training i think i could work out... :-?
The plan is to use the laptop as a picture frame, showing a slideshow.

I have a few requirements:

1. Feh should start automatically on boot 
2. Should be able to upload pictures from another computer (not just lan)
3. When the slideshow is running, i want it to constantly synchronize with the picture folder (if you upload new pictures from another computer)

I think i have correctly installed feh. I have not figured out how the scripting works... Whery basic, how to write script, where to save them and get them to work. 

Found some scripts here: [http://thewares.net/item/33]("http://thewares.net/item/33") , guess i can use some of it, but i just dont know how...

When it comes to number 2., i have installed Opera with Opera unite and planning of using "File Sharing" thing to upload from another computer. So opera need to boot when i turn on the computer as well. 

If you have any input on how to do any of this that would be great! have tried to follow guides online but get lost in the scripting because I just don't understand enough. If someone could offer a starting point (online guides etc...)that would be great.

Have Xfce installed, if its possible to do something in Xfce and not just in the terminal i would be happy.

Thanks in advance!

Excuse my english... ;)

---

### Post by embryo_ on 2009-11-29
Ok, after a bit trying and failing i got some scripts running. 

Im using this script to run the slideshow at boot:
```
root@0[frame]# vi cron_start_frame.sh

#!/bin/sh


# Set display so that the script will effect
# the screen on the frame
export DISPLAY=:0


# Start slide show
feh --quiet --recursive --randomize --full-screen --slideshow-delay 2 --hide-pointer /home/fotoramme/Dokumenter/photos/ &


exit 0
```

The problem now is to get the update script working, found a script on a similar project page, but can not find out how to get it running. The script should automatically check the folder for newly added pictures.

```
root@0[frame]# vi checkdir.sh

#/bin/bash
#monitor directory

mv /home/fotoramme/Dokumenter/photos.lst /home/fotoramme/Dokumenter/photos.last
ls -R /home/fotoramme/Dokumenter/photos > /home/fotoramme/Dokumenter/photos.lst
cmp --quiet /home/fotoramme/Dokumenter/photos.lst /home/fotoramme/Dokumenter/photos.last
exitcode=$?

if [ $exitcode -ne 0 ] ; then
echo &#8220;New Files... Reloading Frame&#8221;
/home/fotoramme/Dokumenter/cron_reload_frame.sh
else
echo &#8220;Yawn...&#8221;
fi

exit 0
``` 

The "cron_reload_frame.sh" code:
```
	root@0[frame]# vi cron_reload_frame.sh

#!/bin/sh
#

# Set display so that the script will effect
# the screen on the frame
export DISPLAY=:0

# Stop the currently running Slide show
/homesad/fotoramme/Dokumenter/kill.sh feh

sleep 1s

# Start slide show
feh --quiet --recursive --randomize --full-screen --slideshow-delay 20 --hide-pointer /home/fotoramme/Dokumenter/photos/ &

exit 0
``` 

So i need some help getting the checkdir.sh working, and i also need some help to get Opera Unite load at boot.

Thanks!

---

### Post by RATM_Owns on 2009-11-29
Try something like:
```
if [ `cat [FONT=monospace]~/[/FONT]Dokumenter/photos.lst` != `cat [FONT=monospace]~/[/FONT]Dokumenter/photos.lst` ] ; then
        ~/Dokumenter/cron_reload_frame.sh
fi
```

I'm not familiar with what cmp does so...

---

### Post by embryo_ on 2009-11-29
Ok, thanks. But do i insert that code into cron_start_frame.sh or should i make new script file for it?

---

### Post by RATM_Owns on 2009-11-29
```
#/bin/bash

mv ~/Dokumenter/photos.lst ~/Dokumenter/photos.last
ls -R ~/Dokumenter/photos > ~/Dokumenter/photos.lst
if [ `cat [FONT=monospace]~/[/FONT]Dokumenter/photos.lst` != `cat [FONT=monospace]~/[/FONT]Dokumenter/photos.lst` ] ; then
        ~/Dokumenter/cron_reload_frame.sh
fi
```Something like that.

---

### Post by XubuRoxMySox on 2009-11-29
Why not just use the slide-show screensaver? From **Settings** go to **Screensaver**, choose **Slideshow** and select the folder with the pictures you want to display. Just an idea...

-Robin

---

### Post by embryo_ on 2009-11-29
I had some faults in the scripts, but this is what i got now:

cron_start_frame.sh
```
root@0[frame]# vi cron_start_frame.sh

#!/bin/sh

export DISPLAY=:0

# Start slide show
feh --quiet --recursive --randomize --full-screen --slideshow-delay 2 --hide-pointer /home/fotoramme/Dokumenter/photos/ &

/home/fotoramme/Dokumenter/cron_checkdir.sh


exit 0
```

cron_checkdir.sh
```
root@0[frame]# vi cron_checkdir.sh

#!/bin/sh
#monitor directory

mv /home/fotoramme/Dokumenter/photos.lst /home/fotoramme/Dokumenter/photos.last
ls -R /home/fotoramme/Dokumenter/photos > /home/fotoramme/Dokumenter/photos.lst
cmp --quiet /home/fotoramme/Dokumenter/photos.lst /home/fotoramme/Dokumenter/photos.last
exitcode=$?

if [ $exitcode -ne 0 ] ; then
echo &#8220;New Files... Reloading Frame&#8221;
/home/fotoramme/Dokumenter/cron_reload_frame.sh
else
echo &#8220;Yawn...&#8221;
fi

exit 0
```

cron_reload_frame.sh
```
root@0[frame]# vi cron_reload_frame.sh

#!/bin/sh
#
export DISPLAY=:0

# Stop the currently running Slide show
killall feh 

sleep 1s

# Start slide show
feh --quiet --recursive --randomize --full-screen --slideshow-delay 2 --hide-pointer /home/fotoramme/Dokumenter/photos/ &

exit 0
```

It seems like the start and reload script is working, but there must be something wrong in the checkdir script...and how do i get them to work all together and to run continuously? I have added the "cron_start_frame.sh" to auto-boot, but when I add new pictures to the folder, the slideshow wont update. 
For me it seems like the script only run once, shouldn't them run over and over again to do the job checkdir i supposed to do? 

Thanks for help RATM_Owns, but Im not sure if its that code im looking for...?

Very basic knowledge all this i guess, but thanks for any help i can get!...

---

### Post by embryo_ on 2009-11-29
Hm, nobody knows? Im not that good in English, and maybe the question isnt clear enough, but any help is good help! :)

---

### Post by embryo_ on 2009-11-30
Anybody?

---

### Post by XubuRoxMySox on 2009-11-30
You want a slideshow, right? Xubuntu has a **slideshow screensaver**. Unless I have completely misunderstood you, it can certainly be set up to start the screensaver within minutes of boot-up and your laptop becomes a digital picture frame.

-Robin

---

### Post by embryo_ on 2009-11-30
Yes, but when the slideshow is running, i want it to automaticly add new pictures to the slideshow. 
Now, if i upload pictures to the picture folder from another computer using Opera Unite, the pictures wont appare in the slideshow before its restarted. So, i need a script to auto-restart the slideshow whenever a new picture is added to the folder.

---

