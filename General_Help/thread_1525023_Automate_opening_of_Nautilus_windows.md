---
title: "Automate opening of Nautilus windows?"
date: 2010-07-06
forum: General Help
---

### Post by startling on 2010-07-06
Every time I start Ubuntu, to enable copying files, I open two Nautilus windows and I then have to drag those windows into the places on the desktop where I'd like them to be. It seems silly to manually do this 800 times a year! Is there any way to automate this? Would a script be able to achieve this?

---

### Post by stinkeye on 2010-07-06
**[COLOR="DarkRed"]Edit:[/COLOR]**You could just use nautilus --no-desktop --geometry=640x480+[COLOR="#8b0000"]50+50[/COLOR]
[COLOR="#8b0000"]x+y[/COLOR] =position.
eg for the same result as the wmctrl method
```
#!/bin/bash
nautilus /home/glen --no-desktop --geometry=830x1025+0+0
nautilus /home/glen --no-desktop --geometry=830x1025+1025+0
```

**_______________________________________________________________________**




You could use wmctrl to achieve this.
```
sudo apt-get install wmctrl
```



I'm not very good at writing scripts but this will open 2 nautilus windows
in split screen for my 1680x1050 resolution.
```
#!/bin/bash


nautilus [COLOR="Purple"]/home/glen[/COLOR]
sleep 3; 
wmctrl -r :ACTIVE: -e 0,0,0,830,1025
sleep 1; 
nautilus [COLOR="#800080"]/home/glen[/COLOR]
sleep 1;
wmctrl -r :ACTIVE: -e 0,1025,0,830,1025
```

You could add this as a panel launcher.(make the script executable)
Just change the [COLOR="#800080"]directories[/COLOR] and adjust the wmctrl
settings for your resolution and how you want your windows to be displayed.

This post will help you with the wmctrl settings: [**_http://ubuntuforums.org/showpost.php?p=8444754&postcount=5_**]("http://ubuntuforums.org/showpost.php?p=8444754&postcount=5")

---

### Post by sidewalkcynic on 2010-07-06
Seems like you should be able to do it with the Start-Up application from the preferences menu.

---

### Post by startling on 2010-07-07
Brilliant! Thanks stinkeye - that works a treat!

---

