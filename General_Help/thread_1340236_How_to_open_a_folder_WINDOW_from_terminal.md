---
title: "How to open a folder WINDOW from terminal?"
date: 2009-11-28
forum: General Help
---

### Post by bit mad on 2009-11-28
Suppose I'm in a terminal, or a script, and I want to open windows of two folders? What command would do that?

In a Windows command line or batch you can [COLOR=Blue]start .[/COLOR] and a folder window will appear, of the current directory - or use  [COLOR=Blue]start \temp[/COLOR]  to open that temp folder for example. The batch file carries on doing its thing, leaving the folder window on screen. 

Why? Well, I'd like to be able to open a folder where my Firefox settings are saved on my Windows volume, and also see the contents of  ~/.mozilla/firefox/ so that I can open the randomly named folder there and then copy from one to the other (I guess I'd also need the option set to Show Hidden/System files too?)

All this is to do with running from a Live CD, and being able to get settings and prefs copied over in a simple script file so that it can all be just as I like it without needing 'persistence'. So far I've managed to get a script running to copy over a better **xorg.conf** and **gconftool-2 --load** to get things set up nicely, so I'm working on Firefox now.

I have since found [http://support.mozilla.com/en-US/kb/Backing+up+your+information](http://support.mozilla.com/en-US/kb/Backing+up+your+information) and the useful info there about *profiles.ini* which I might be able to use, to automate it... but I'd like to know how to do the above anyway, if you'd be so kind please :)
Thanks

---

### Post by NoaHall on 2009-11-28
```
nautilus ~/.mozilla/firefox/
```

---

### Post by bit mad on 2009-11-28
Thanks - I guess that's probably obvious with hindsight, LOL

I tried  **nautilus --help**  but there doesn't seem to be a way to force showing hidden files. Oh well, *Ctrl-H* will have to do :D

Many thanks

---

### Post by bit mad on 2009-11-28
I found a way to do it. I keep the following *firefox-setup.sh* script on my Windows drive, where the Firefox settings have been previously copied to C:\mint\firefox\

In my initial setup script I now copy this script onto the desktop with 
```
# copy Firefox setup script onto desktop for ease of running
sudo cp /media/disk/mint/firefox-setup.sh  /home/mint/Desktop/
```

*firefox-setup.sh*
```
#!/bin/bash

# run firefox so that it will set up folders, I will close it manually
firefox

function pause(){
   read -p “$*”
}
echo "Close Firefox first..."
pause 'Press_any_key'

cd /home/mint/.mozilla/firefox
for dir in ????????.default ; do cd $dir ; done
pwd
pause 'Press_any_key___if_firefox_folder_correct'

sudo chown mint *.*
sudo cp --remove-destination /media/disk/mint/firefox/*.* .
sudo chown mint *.*

ls -l
pause 'hope_that_worked!'
#nautilus .

```

That seems to do the trick :D
After loggin in, the script is on the desktop. I run it, close the first Firefox that appears, continue the script and the next time I run Firefox it comes up with my toolbar prefs, homepage, etc. Yay!

---

