---
title: "startup script for trackpad"
date: 2010-08-26
forum: General Help
---

### Post by brettdunnam on 2010-08-26
in order to get my trackpad's (eeepc 1201n, ubuntu desktop 10.04) multitouch scrolling to work, i paste these commands into the terminal every time i start the machine:
```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
```

i want to turn this into a script that runs on startup and the process that seems to be the "proper way" isn't working for me so i was hoping someone could fill me in as to what i'm doing wrong. here are the steps i take:

first, create and save a file (i called it trackpad) in /etc/init.d/ with these contents:
```
#!/bin/sh
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
```

then make that file executable:
```
chmod +x /etc/init.d/trackpad
```

then make it run on startup:
```
update-rc.d trackpad defaults
```

after i do all those things and restart the machine, nothing is different. i can still use the synaptic side scrolling or enter the commands manually into terminal and get multitouch again. i'm pulling my hair out over this because i know i'm dumb and something simple is wrong.

---

### Post by brettdunnam on 2010-08-26
Okay so this was WAY easier than I thought. There are three simple steps to make the trackpad work.

1. Create a file and save it wherever you want with these contents:
```
#!/bin/sh
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
```

2. Make it executable with chmod +x
```
sudo chmod +x /path/to/file
```

3. Add the file to Startup Applications in System>Preferences>Startup Applications

---

### Post by BEKO86 on 2011-01-06
Thanks man just got my 1201NL today hopefully this will fix multitouch.

---

### Post by BEKO86 on 2011-01-06
Nah didnt work for me on 10.10.

---

### Post by shopfreelancer on 2011-01-25
The mentioned solution didn't work for me on my Asus EEE PC 1005PX. Whenever I typed the commands into the shell it worked fine but somehow the same commands in a file weren't executed. It took me the whole afternoon and I tried a couple of other solutions (just a curious user) till I came to a possible explanation: The xinput tool is not launched yet when the auto start commands are executed. I found the solution for the shell script in the German forum[http://forum.ubuntuusers.de/topic/touchpad-bildlauf-mit-2-finger-geht-nicht-thi/2/](http://forum.ubuntuusers.de/topic/touchpad-bildlauf-mit-2-finger-geht-nicht-thi/2/) for a Thinkpad. The trick is to add a delay to the above code. So the following code works fine for me in a file added to the start applications (see post #2).
```

#!/bin/bash

sleep 05

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8

exit 0

```

EDIT: The mentioned solution does work for the regular boot sequence but is gone when you're system is restarted from sleep mode. I've been dealing with this problem even longer and the solution that worked for me finally can be found here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308191/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308191/+index?comments=all) Comment #116.

---

### Post by JoshBarnett92 on 2011-02-21
Is there anyway that someone could give me step by step directions on how to enable 2 finger scrolling/pinching? I have already fixed the right click problem. I am running Ubuntu 10.04 netbook remix on an hp mini. I have dual OS's also with vista as the other. I have no problem using 2 finger scrolling on vista, but this is my first try at linux and I don't understand what you guys are saying to do. Thanks

---

### Post by cylent on 2013-01-20
cool

but i added a new line to make it somewhat better...

```
#!/bin/sh
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Finger" 55 60 255
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
```

---

