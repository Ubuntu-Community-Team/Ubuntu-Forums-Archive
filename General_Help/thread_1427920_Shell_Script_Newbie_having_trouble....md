---
title: "Shell Script Newbie having trouble..."
date: 2010-03-12
forum: General Help
---

### Post by BananaPeal on 2010-03-12
Hi everyone, 

I recently modified a shell script I found on the internet to change the background :popcorn: . I'm running it with gnome-schedule and every time it runs it leaves behind a terminal window asking you to 'push enter to exit'

Is there a command I need to add to the script to have the terminal close automatically once it's done?

Thanks for your help,

Alex

running  ubuntu 9.04 gnome

---

### Post by diesch on 2010-03-12
Most likely you need to remove something from the script, but that's hard to know without seeing the script.

---

### Post by BananaPeal on 2010-03-12
Hello again,

Sorry about the lack of details! Here's my script and some more symptoms:

PIC=$(ls ~alex/Pictures/wallpaper/*.jpg | shuf -n1)
gconftool-2 --set /desktop/gnome/background/picture_filename -t string $PIC
exit

its permissions:
-rwxr-xr-x  1 alex alex  133 2010-03-12 04:56 changeWallpaper

when running it in terminal as ~$ bash changeWallpaper, it works as expected. 

when changing the timing on scheduled tasks to every minute, nothing happens.

when clicking the 'run task' button it changes the wall paper and leaves a terminal window open.

the task to be run is simply: bash changeWallpaper as above and for some reason unchecking the "no output"  button (in 'edit a scheduled task') makes it work. With it checked, the background doesn't change.

Wow. didn't mean for this to be too long... I've only had Linux for a few hours and just taught myself the scripting from examples without learning the rules that might dictate this behavior.

Seems simple enough though huh? Those literally are all the details as far as I know, any ideas as to why it's not going quite as smoothly? It works everytime from the command prompt...

Thanks for your help!

---

