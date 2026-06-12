---
title: "Running script by pressing key on bluetooth Remote Control"
date: 2010-09-03
forum: General Help
---

### Post by abid_naqvi83 on 2010-09-03
I have a Dell Inspiron E1705 running Ubuntu 9.10. I also possess an Interlink VP6600 Media Remote Control (Bluetooth) which Ubuntu detects and displays under Bluetooth Devices. Furthermore the Volume and Media controls work as advertised, so no problems there. 

My objective is to be able to press one of the **little used** buttons on the bluetooth Remote Control and cause that action to execute a small script of my own devising which basically speaks the current time out loud. (The idea is to use this while in bed at night - I have glasses and looking at the clock isn't very helpful.)

The script is located at /home/<user>/.bin/speak_time.sh and it contains:

```
#!/bin/bash

# This script speaks the current time

echo "The time is" `date "+%l %M"` | espeak -s 100

```

I know very little about interfacing with bluetooth devices but learn fast. A little ferreting about over the internet revealed things like 'hcitoo', 'hidd' and 'xmodmap' which I couldn't quite understand.

A detailed explanation of how any presented solution works would be most appreciated and should be of use to both present and future enthusiasts. Thanks in advance.

---

### Post by abid_naqvi83 on 2011-01-24
It took me a while but I figured it out in the end. It was quite simply actually since the Remote was already interfacing with the OS and it was being treated like an input device (sort of like a multimedia keyboard).

Most of the relevant information was extracted from the following sites:

[http://en.gentoo-wiki.com/wiki/Multimedia_Keys#Setting_up_xmodmap]("http://en.gentoo-wiki.com/wiki/Multimedia_Keys#Setting_up_xmodmap")   
[http://www.howtoforge.com/linux_multimedia_keyboard]("http://www.howtoforge.com/linux_multimedia_keyboard")


The gist of it is that I first used 'xev' to figure out the keycode assigned to the various keys on the Bluetooth Remote, particularly for the key I intended to use (216 in my case).

The next step was to create and edit the 'xmodmap' configuration file (~/.Xmodmap which can be generated using the command 'xmodmap -defaults > ~/.Xmodmap' and commenting out the example connections) to forge a connection between the relevant keycode and an unused keysym (a symbolic key which Linux uses as a handle on certain common actions such as XF86Play and XF86Mute etc.) I connected the keycode for my Bluetooth Remote button to the XF86Time keysym which as far as I could determine wasn't doing anything in ~/.Xmodmap:

```
keycode 216 = XF86Time
```

I ran ```
xmodmap ~/.Xmodmap
``` to load the connection. (This doesn't stick so one has to restart the computer exactly once for the X session to start picking up the .Xmodmap file.)

The final step was to connect the XF86Time keysym to the user script speak_time.sh by first installing 'xbindkeys' from Synaptics and then creating and modifying its configuration file (~/.xbindkeysrc) to contain the following lines:

```
"<full path to file>/speak_time.sh"
XF86Time
```

'xbindkeys' must be called every time the X session is loaded for this to work. I simply put a call to xbindkeys in System > Preferences > Startup Applications. 

And now every time I press the relevant key on my Bluetooth Remote the computer tells me the current time.

---

