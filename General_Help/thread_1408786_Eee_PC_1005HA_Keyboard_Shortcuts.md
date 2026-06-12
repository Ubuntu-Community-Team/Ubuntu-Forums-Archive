---
title: "Eee PC 1005HA Keyboard Shortcuts"
date: 2010-02-16
forum: General Help
---

### Post by cambunctious on 2010-02-16
Some of the shorcuts work but some don't like Sleep, Disable Touchpad, Turn off Monitor.  I've tried installing the eeepc-acpi-scripts package but it won't install.

[I]eeepc-acpi-scripts:
 Depends: acpi-support-base  but it is not installable[/I]

I found [this nifty little tutorial]("http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/") but I don't know how to use Fn keys with it.

Any advice?  Thanks!

---

### Post by tophatandy on 2010-02-18
I am interested in the exact same thing. I mostly want to regain the additional "touchpad off" key that is detached from the keyboard if possible. (I hate how I tap the touchpad when I am trying to type, so that key comes in handy big time with writing papers and whatnot)

I will hunt as well, and if I gather anything I will def. post it up here. :)

---

### Post by pi/roman on 2010-02-18
You can create a script to toggle the touchpad as I have here:
[[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=1401645[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1401645") in addendum section b: toggle shortcut.
> # toggle synaptic touchpad on/off
# get current state
SYNSTATE=$(xinput list-props "SynPS/2 Synaptics TouchPad" | grep Enabled |  grep -Eo '.$')
# change to other state
if [ $SYNSTATE = 0 ]; then
    xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1
elif [ $SYNSTATE = 1 ]; then
    xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0
else
    echo "i give up"
    exit 1
fi
exit 0
use the name of your touchpad in all 3 places, make that executable and place it in /usr/bin then you can either run it by pressing alt/f2 and typing the name of the script or make a shortcut key combination in gnome-keybinding-properties using the name of the script as a command then use your touchpad off key as the toggle or any other key combination.

---

### Post by RemiemB on 2010-04-29
I tried the following:

1. Uninstalled **[COLOR="Red"]acpi-support[/COLOR]** from Synaptic
2. Downloaded and installed **[COLOR="red"]acpi-support-base[/COLOR]** from: [**[COLOR="Blue"]here[/COLOR]**]("http://www.filewatcher.com/b/ftp/ftp.gnome.org/cdimage/snapshot/Debian/pool/main/a/acpi-support.0.0.html")
3. Installed **[COLOR="red"]eeepc-acpi-scripts[/COLOR]** from Synaptic. 

Now, just a few other keys work. I'm working on it...

Someone else try it post some feedback! Thanks!

---

