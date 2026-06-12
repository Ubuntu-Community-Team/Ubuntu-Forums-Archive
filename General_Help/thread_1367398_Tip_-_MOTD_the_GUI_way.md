---
title: "Tip - MOTD the GUI way"
date: 2009-12-29
forum: General Help
---

### Post by tkoco on 2009-12-29
The Ubuntu Forum has a lot of great tips for MOTD display and mods. Unfortunately, all of them require a terminal window like Xterm. I needed to display the MOTD on the Gnome desktop after the desktop started. Not to be deterred, I searched for a ready made solution. Alas, none were to be found. So here is my solution for the Ubuntu community to enjoy. The program is written in python and requires python-tk. The fortune and/or cowsay packages are optional, if you want them displayed as well. 

```

#!/usr/bin/python
## motd_gui  -  A MOTD program for GUI desktop
## Written by Thomas Kocourek 2009
## Released under GPL License for all
## Requires Python and Python-tk
##
## Set the executable permission and store in
## /usr/bin directory
## Use the Gnome System > Preferences > Startup Applications > Add
## to add this program to the desktop

import Tkinter
import os

## The file can be any multi-line text file
## edit the filename as you wish
m_file = open('/etc/motd.2')
motd_data = m_file.readlines()
m_file.close()
motd = ""
for data in motd_data:
	motd = motd + data

## for those who wish to add a fortune or cow says
## You will have to install 'fortune' and cowsay' packages
## Be warned, the spacing of characters is not the same as xterm
## Uncomment the next 5 lines
#m_file = os.popen('fortune -s | cowsay -n -f udder.cow ')
#f_data = m_file.readlines()
#m_file.close()
#for data in f_data:
#	motd = motd + data

wind = Tkinter.Tk()
data = Tkinter.Label(wind, text = motd)
data.pack()
Tkinter.mainloop()

```

Enjoy!

---

