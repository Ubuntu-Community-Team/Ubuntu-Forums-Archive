---
title: "Changing log-in Wallpaper in 10.04 and up"
date: 2011-07-25
forum: General Help
---

### Post by munchen800 on 2011-07-25
I just wrote a little script to help anyone out if they want to do this.  
Just download loginWallpaper.sh

open your terminal and cd to the download directory  

run 
```
sudo chmod 744 loginWallpaper 
```then run 
```
./loginWallpaper.sh  
```and follow the prompts  
Make sure the pic you want to use is a .JPG and is in your home directory. Choose Option 1 on your first run. It will move the pic to the proper directory on the system and will open the Gnome Appearance Preferences at the log-in screen. After you run Option 1 logout, goto Background then Add button. Select your wallpaper and "BOOM" it changes. Log back in and run the script again 
```
./loginWallpaper.sh
``` only use Option 2 to keep the Gnome Appearance Preferences from opening again.

---

### Post by Kallun on 2011-07-25
Very nice! This'll come in handy :)

---

