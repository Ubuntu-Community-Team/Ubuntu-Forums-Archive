---
title: "inhibit applet command line?"
date: 2010-05-16
forum: General Help
---

### Post by princeofnam on 2010-05-16
does anyone know what command i could type to turn on and off a function similar to the "inhibit applet" on the top panel?  my screen keeps dimming while viewing on VLC and i often prefer to avoid using the mouse

---

### Post by CurlyTorky on 2010-11-23
Sorry for my vary bad english...

Command:
```
gconftool --type int -s /apps/gnome-power-manager/backlight/idle_dim_time 0 && gconftool --type int -s /apps/gnome-power-manager/timeout/sleep_display_battery 0 && gconftool --type int -s /apps/gnome-power-manager/timeout/sleep_computer_battery 0
```

gconftool --type int -s /apps/gnome-power-manager/backlight/idle_dim_time ***time***

gconftool --type int -s /apps/gnome-power-manager/timeout/sleep_display_battery ***time***

gconftool --type int -s /apps/gnome-power-manager/timeout/sleep_computer_battery ***time***

you can make a script:

```
#!/bin/sh
if [ -e /tmp/inhibit ]; then
gconftool --type int -s /apps/gnome-power-manager/backlight/idle_dim_time 10
gconftool --type int -s /apps/gnome-power-manager/timeout/sleep_display_battery 300
gconftool --type int -s /apps/gnome-power-manager/timeout/sleep_computer_battery 600
rm /tmp/inhibit
else
gconftool --type int -s /apps/gnome-power-manager/backlight/idle_dim_time 0
gconftool --type int -s /apps/gnome-power-manager/timeout/sleep_display_battery 0
gconftool --type int -s /apps/gnome-power-manager/timeout/sleep_computer_batter 0
touch /tmp/inhibit
fi
```

or a more elaborate:

```
#!/bin/sh
idle=10
display=300
computer=600
title_on="Hi "
title_off="Bye "
 
if [ $1 = "off" ]; then
gconftool --type int -s /apps/gnome-power-manager/backlight/idle_dim_time $idle
gconftool --type int -s /apps/gnome-power-manager/timeout/sleep_display_battery $display
gconftool --type int -s /apps/gnome-power-manager/timeout/sleep_computer_battery $computer
rm /tmp/inhibit
else
    if [ -e /tmp/inhibit ]; then
        gconftool --type int -s /apps/gnome-power-manager/backlight/idle_dim_time $idle
        gconftool --type int -s /apps/gnome-power-manager/timeout/sleep_display_battery $display
        gconftool --type int -s /apps/gnome-power-manager/timeout/sleep_computer_battery $computer
        notify-send --icon=/home/torky/Immagini/Icons/sleep_128.png "$title_off" "idle_dim_time: $idle; sleep_display_battery:$display; sleep_computer_battery: $computer"
        rm /tmp/inhibit
    else
        gconftool --type int -s /apps/gnome-power-manager/backlight/idle_dim_time 0
        gconftool --type int -s /apps/gnome-power-manager/timeout/sleep_display_battery 0
        gconftool --type int -s /apps/gnome-power-manager/timeout/sleep_computer_battery 0
        notify-send --icon=/home/torky/Immagini/Icons/coffe/1290031116_coffee-cup.png "$title_on" "idle_dim_time: 0; sleep_display_battery: 0; sleep_computer_battery: 0"
        touch /tmp/inhibit
    fi
fi
```

this restores the default values at the system startup, but you have to add to the startup the command "(script name) off"

if the script's name is toggleinhibit --> toggleinhibit off

for notifications you have to install libnotify-bin:
```
sudo apt-get install libnotify-bin
```

for icons you have to write the correct directory...

Ciao Ciao :D

---

### Post by NoelJB on 2011-01-04
The solutions provided are **not** equivalent to the Inhibit Applet, which is also missing from Natty (and Fedora 14).

The correct way to inhibit is to use an interface to the Session Manager.  I have written a quick and dirty command-line toggle to do this, which you can download: [toggleinhibit]("http://www.devtech.com/toggleinhibit").  Mind you, it has to be run such that it stays loaded.  As soon as the python process exits, the session manager will discard the inhibits as being "orphaned."

I have also written an App Indicator applet to do this, which you can download: [inhibitapplet]("http://www.devtech.com/inhibitapplet").  Hopefully, we can get this into Natty and later.

---

