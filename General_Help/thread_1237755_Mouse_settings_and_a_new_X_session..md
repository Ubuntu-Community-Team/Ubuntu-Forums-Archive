---
title: "Mouse settings and a new X session."
date: 2009-08-11
forum: General Help
---

### Post by foogs on 2009-08-11
I'm fairly new to Ubuntu. I've searched around as much as I could and I'm having troubles figuring this out on my own.

In gnome I have my mouse settings set up exactly how I would like them. I have acceleration disabled from the Gnome Mouse Preferences program. I also use xset m 0 0 as a startup application just to make sure it's turned off (I don't know if this is redundant or not even needed). The reason I want acceleration turned off is because it's horrible for any type of gaming you try to do. I personally play Starcraft.

Now this is great cause I can play Starcraft without any mouse acceleration when I start Starcraft from gnome. If I try to start starcraft using a script (It opens a new X session in starcraft so I can alt tab back and forth) I lose all of my mouse sensitivity settings.

Heres the script that I'm using scstart.sh (referenced here: [http://ubuntuforums.org/showthread.php?t=822888](http://ubuntuforums.org/showthread.php?t=822888))

```
#!/bin/sh

# If found isn't working, try uncommenting these two lines
#sudo adduser $USER pulse-rt # logout after this
#sudo chmod 777 /dev/snd/seq

# Kill previous instances
ps auxf |grep SCLayout | grep -v grep | awk '{print "kill -9 "$2}' |bash

# Start new X
X :1 -layout SCLayout -ac &
XPID=$! & xset m 0 0
sleep 2

# Do Volume Key Control mapping if set up 
if [ -f $HOME/.scbind ]; then
    xbindkeys --display :1 -f $HOME/.scbind
fi

# Start Pulse Audio & Starcraft in new X
sudo /etc/init.d/hal restart

DISPLAY=:1 ck-launch-session wine $HOME/.wine/drive_c/Program\ \Files/Starcraft/StarCraft.exe -- /usr/bin/X :1 -layout SCLayout & unclutter -display :1 -root & xset m 0 0

# Cleanup
sleep 1
kill $XPID
```So I think my question would really be: How do I take my main mouse settings (the mouse settings im using in gnome) and transfer them over to a new X session? Thanks for your time. Hopefully when I'm more versed in this operating system I'll be able to help other people out too!

---

### Post by foogs on 2009-08-11
I tried turning off acceleration the way I think I'm supposed to and it didn't work. Per the[ X.Org wiki]("http://www.x.org/wiki/Development/Documentation/PointerAcceleration")  advice I should set AccelerationProfile to -1.
> -1 **none** 
no velocity-dependent pointer acceleration or deceleration. If constant deceleration is also unused, motion processing is suppressed, saving some cycles.When I unplugged my mouse in and then out it crashed X and I had to delete the fdi I created below to be able to boot back into gnome.

```
<match key="info.product" string="Razer Razer Salmosa">
 <merge key="input.x11_options.AccelerationProfile" type="string">-1</merge>
</match>
```Does this happen to anyone else when they try to do it? Did I find a bug?

Other values like 4 and 2 work fine, but -1 crashes X. Here's an output from when I have it set to 4.

```
(II) XINPUT: Adding extended input device "Razer Razer Salmosa" (type: MOUSE)
(**) Razer Razer Salmosa: (accel) keeping acceleration scheme 1
(**) Razer Razer Salmosa: (accel) filter chain progression: 2.00
(**) Razer Razer Salmosa: (accel) filter stage 0: 20.00 ms
(**) Option "AccelerationProfile" "4"
(**) Razer Razer Salmosa: (accel) set acceleration profile 4
```

What the heck does keeping acceleeration scheme 1 mean? Is there any documentation on this anywhere. I've searched google but no luck.

---

### Post by foogs on 2009-08-12
Saved this as /etc/hal/fdi/policy/mouse.fdi and my acceleration/sensitivity settings havent changed since even when in a new x session running starcraft. all is well.

This is for a Razer Salmosa mouse

```
<?xml version="1.0" encoding="ISO-8859-1"?>
  <device>
    <match key="info.product" string="Razer Razer Salmosa">
    <merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
        <merge key="input.x11_options.AccelerationProfile" type="string">1</merge>
        <merge key="input.x11_options.AccelerationScheme" type="string">none</merge>
    </match>
  </device>

```

---

### Post by captaincrook on 2009-08-12
Question on this topic of mice settings.

Currently using the XFCE DE, would it be possible to have X or something save the current mouse settings for use with a different desktop environment and it would be the same? It seems like its possible with the above post but I don't wanna goof up or whatever.

---

