---
title: "remote mouse via lircmd"
date: 2011-07-04
forum: General Help
---

### Post by DanBender on 2011-07-04
I'm trying to set up a remote control mouse via lircmd, but I'm not finding *great* documentation to go along with it.

First of all, I believe lirc itself is set up correctly. I'm running Mythbuntu 10.10, and when I plug in my USB remote receiver, it drives MythTV just fine. The selection in Mythbuntu Control Centre is "Windows Media Center Transceivers/Remotes (all)," and the remote I'm using is a Logitech Harmony 550 emulating a generic WMC remote. So I *believe* I only need to get the mouse stuff working.

Anyway, how do I determine whether or not I have the correct stuff installed or running? I suspect it's installed (it would make a lot of sense, being Mythbuntu and all), and there is /etc/lirc/lircmd.conf, and there's a man entry for lircmd. These indicate to me that it is installed, and only needs to be configured and called. There is *not* a device /dev/lircm, so it seems to me it's not currently running. The documentation provided says some stuff needs to be added to XF86Config, which I can't find, [this thread]("http://ubuntuforums.org/showthread.php?t=1148530") indicates either add something similar to Xorg.conf (which I also can't find) or some stuff to do in hal. Not sure the best approach, and not sure if anything else would need to be done (I need this to be running on every login).

And once I figure out if it's running / how to get it running, I still need to get it configured. There's an example in /usr/share/doc/lirc, which I think I can base my configuration on. However, I'm not sure what the valid commands are from a generic WMC remote. The example uses stuff like ARROW_LEFT and OK; if that's valid syntax for my remote I'm sure the mouse movement and button press will be pretty straightforward, but I need to make sure I set something for mouse-mode toggle that is: valid, won't be needed for something else, and can be assigned in the Harmony software. Is there a list of valid commands for a WMC remote I can use for reference?

Thanks in advance for any help y'all can give me.
-Dan

---

### Post by DanBender on 2011-07-06
Hmmm...I appear to have done something, but it's hard to tell what. I opened a full-screen terminal (Ctl-Alt-F1) and ran```
sudo service gdm stop
sudo Xorg -configure
```and it placed Xorg.conf.new in my home directory. It then said to do something like```
sudo X -configure Xorg.conf.new
```which I did, but it didn't seem to start any graphical anything; it just threw up a bunch of stuff in that terminal, so I did a sudo reboot from the next terminal and the computer started just fine, graphics and all. Except after that I was able to delete the Xorg.conf.new in my home directory while the graphics were still running (from the graphical file manager, *not *using a sudo rm) - does that mean it wasn't being used? Is there a better way to generate an Xorg.conf to my current setup (that will then be used automatically on login, so that I can edit it for the lircmd stuff), or do I just need to copy it to a certain location?

Part of this process made the remote not work in MythTV, but I'm not sure which. The activity light on the receiver flashes when it gets a signal, though, so I think it just stripped the control assignments from within MythTV somehow rather than breaking lirc outright (the setup->edit keys doesn't show any remote commands assigned to the functions anymore, except for volume keys for some reason). If that's what it was (I'll look at it tomorrow) I can reassign keys well enough; it just seems odd.

---

### Post by DanBender on 2011-07-08
Heh, it looks like I have an xorg.conf after all...it's just xorg.conf, not Xorg.conf. Dang you *NIX and your case sensitivity!

...and it even looks like I had a post on creating one more than a year ago. That makes me feel just a little stupid, since it answered that question and spelled out exactly what I was asking about in the last post.

Anyway, guess I'll try doing that manual edit to the file, or that hal business. Not sure which sounds like a better way yet, though.

---

### Post by DanBender on 2011-07-13
Alright, I've made progress, but I'm not sure I've...made any progress.

I added the following to my /etc/X11/xorg.conf file:

in the ServerLayout section:```
    InputDevice    "LIRC-Mouse"
```after my normal mouse entry:```
Section "InputDevice"
        Identifier  "LIRC-Mouse"
        Driver      "mouse"
        Option      "Device" "/var/run/lirc/lircm"
        Option      "Protocol" "IntelliMouse"
        Option      "SendCoreEvents"
        Option      "Buttons" "5"
        Option      "ZAxisMapping" "4 5"
EndSection
```I used irw to determine the correct codes for my remote (as of what Harmony assigned to the keys):
```
000000037ff07be1 00 Up mceusb
000000037ff07be1 01 Up mceusb
000000037ff07be0 00 Down mceusb
000000037ff07be0 01 Down mceusb
000000037ff07bdf 00 Left mceusb
000000037ff07bdf 01 Left mceusb
000000037ff07bdf 02 Left mceusb
000000037ff07bde 00 Right mceusb
000000037ff07bde 01 Right mceusb
000000037ff07bde 02 Right mceusb
000000037ff07bdd 00 OK mceusb
000000037ff07bdd 01 OK mceusb
000000037ff07bdd 02 OK mceusb
000000037ff07bd6 00 BD6 mceusb
000000037ff07bd6 01 BD6 mceusb
```I've edited /etc/lirc/lircmd.conf to the following:```
PROTOCOL IntelliMouse
#PROTOCOL MouseSystems

# ACCELERATOR start max multiplier

ACCELERATOR 2 30 5

TOGGLE_ACTIVATE * BD6

MOVE_N  * Up
MOVE_E  * Right
MOVE_S  * Down
MOVE_W  * Left

BUTTON1_CLICK * OK
```Now, when I restart the computer, lircm does not exist anywhere. I need to sudo lircmd /etc/lirc/lircmd.conf, then it appears in /var/run/lirc/ (which is where the actual file lircd is; /dev/lircd is a link). Unfortunately, after this, when I press the key I assigned to [BD6]...nothing happens. irw continues to respond to keypresses, but the mouse pointer doesn't move. Does anyone have any wisdom regarding this?

And, once I figure out how to get this running at all, I will need to make sure it automatically starts on startup. I suspect the best time to do that would be immediately after lirc begins, but I will need some guidance as to how to accomplish that.

Thank you to anyone who can help,
-Dan

---

### Post by DanBender on 2011-07-16
Okay, followed some of the other steps laid out in [this thread, post 25.]("http://ubuntuforums.org/showthread.php?t=1329662&highlight=lircmd+hal&page=3") Appears to work great.

---

