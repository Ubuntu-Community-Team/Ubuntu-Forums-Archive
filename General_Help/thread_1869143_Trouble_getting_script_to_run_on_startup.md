---
title: "Trouble getting script to run on startup"
date: 2011-10-25
forum: General Help
---

### Post by MobileTechie on 2011-10-25
Hi

I've an ASUS EEE PC 1001P. I've installed JoliOS 1.2 on it. Multitouch does not work and is greyed out in the mouse settings.

I found the following script to fix this:

```
#!/bin/sh
#
# Use xinput --list-props "SynPS/2 Synaptics TouchPad" to extract data
#

# Set multi-touch emulation parameters
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1

# Disable edge scrolling
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 8 0 0 0 

# This will make cursor not to jump if you have two fingers on the touchpad and you list one
# (which you usually do after two-finger scrolling)
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 32 110
```

I saved this as multitouch.sh in my home directory and set it's permssions: chmod 007 multitouch.sh. If I open a terminal from the GUI (as opposed to using Ctrl-Alt-F2) and run this by entering ./multitouch.sh then this fixes the multitouch problem. Great.

So now I want to run this on startup and read [THIS]("http://www.ubuntu-howto.info/howto/how-to-execute-a-command-program-or-script-at-startup-init-mini-howto"). However this does not work on the next restart.

To test the scipt in /etc/init.d I try running from there using a terminal I've brought up my Ctrl-Alt-F2 and I get the error "cannot connect to X server". I've looked this up and apparently I need to add export DISPLAY=:0.0 to the script. I assume this is something to do with the terminal not being opened from the GUI?

Anyway, the script now runs with no error but it doesn't fix the multitouch. It does work OK when run from a GUI-launced Terminal.

What is wrong here and how can I fix it?

Also, why, when I'm in the directory the script is in, do I need to add ./ to the name of the script to get it to run, e.g. ./multitouch.sh? 

Many thanks

---

### Post by gsmanners on 2011-10-25
Rather than using init, I think you should be using ~/.xinitrc (since you're trying to modify how X is functioning).

See: [https://wiki.archlinux.org/index.php/Xinitrc](https://wiki.archlinux.org/index.php/Xinitrc)

I don't know how Joli works, but if it has something like Sessions and Startup in its settings, then you could use that rather than even xinitrc.

---

### Post by MobileTechie on 2011-10-26
I can't find that file nor do I really understand what to do.

Surely it can't be that hard to run a script like this at start up in ubuntu?

---

### Post by gsmanners on 2011-10-26
It isn't "hard," but there is a question of what type of desktop you have. The desktop (among other things) launches X, which is what you are trying to modify. If the desktop has a way of launching things at the start of a session, use that.

---

### Post by MobileTechie on 2011-10-26
It has the usual ubuntu start up applications tool but adding	
the script to it does not work.

I don't know how to progress from this point.

---

### Post by MobileTechie on 2011-10-29
Anyone able to help or to point in the direction of a place that has people who can help?

Thx

---

### Post by alco75 on 2011-10-29
If you've set the bash script as executable, one option is just to add it as a start up programme.

Another option could be to just add those lines of xinput configuration to ~/.profile and they'll be executed at login.

---

