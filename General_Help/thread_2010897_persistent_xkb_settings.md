---
title: "persistent xkb settings"
date: 2012-06-26
forum: General Help
---

### Post by n00ne on 2012-06-26
I'm trying to update my xkb settings for my system after updating to 12.04
if I use setxkbmap to make the settings everything working fine
but even tho I changed the keyboard setting file the changes won't stick after restart 
I think I'm changing the wrong file but I couldn't find where the configuration file is

my keyboard config files is as follows ->
```
$cat  /etc/default/keyboard 
# If you change any of the following variables and X is configured to
# use this file, then the changes will become visible to X only if udev
# is restarted.  You may need to reboot the system.

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.

XKBMODEL="pc105"
XKBLAYOUT="us,il"
XKBVARIANT=","
XKBOPTIONS="grp:alt_shift_toggle,grp_led:scroll"

# If you don't want to use the XKB layout on the console, you can
# specify an alternative keymap.  Make sure it will be accessible
# before /usr is mounted.
# KMAP=/etc/console-setup/defkeymap.kmap.g
```

but if I look at the xkb settings after restart its diffrent ->
```
$ setxkbmap -print
xkb_keymap {
        xkb_keycodes  { include "evdev+aliases(qwerty)" };
        xkb_types     { include "complete"      };
        xkb_compat    { include "complete"      };
        xkb_symbols   { include "pc+us+inet(evdev)"     };
        xkb_geometry  { include "pc(pc105)"     };
};

```

---

### Post by LewisTM on 2012-06-26
Do you have other settings that might conflict with your setxkbmap?
Like Xfce4-settings-manager/Keyboard or the panel xkb plugin?
Ideally you would set the Keyboard settings to use System defaults and then set everything manually, either through a command or the panel plugin.

Cheers!

---

### Post by n00ne on 2012-06-26
I tried using the Xfce4-settings-manager/Keyboard and it doesn't seem work at all (it is now set to system default). 
I used the panel plugin and it seems to work but I can't set it to use the led settings. so I preffer not to use it and set my own configuration (so I removed the plugin from the panel). 

I also tried to add this settings to /etc/X11/xorg.conf
```
Section "InputDevice"
   Identifier  "Keyboard0"
   Driver      "kbd"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us,il"
        Option      "XkbOptions" "grp:alt_shift_toggle,grp_led:scroll"
EndSection

```
but it didn't work

I still can't find where to change the settings so they'll stick.
if this is a setting conflict issue how can I see whats causing the conflict ?

---

### Post by LewisTM on 2012-06-26
One workaround is to manually edit your ~/.config/xfce4/panel/xkb-plugin-##.rc file (the ## varies).
First insert the plugin in a panel and set your preferences.
In the .rc file you should find a line beginning with [FONT="Courier New"]toggle_option=<some option>[/FONT]
Edit it so it shows
```
toggle_option=grp:alt_shift_toggle,grp_led:scroll
```
and save the file.
Reload the plugin with 
```
pkill xkb
```
Your new option should now be applied.
The plugin won't like this extra option but if you *never open the preferences dialog* it should leave it alone. Make a backup of the .rc file just in case.

Hope this works for you.

---

### Post by n00ne on 2012-06-26
thanks but it didn't work.
after issuing pkill the plugin will reload
and everything will work just fine

but after I restart my computer the file 
was rewriten with its original value and the led stoped working.

I wrote a shell script to run setxkbmap with the right parameters
and I can add it to run with when the session starts.
I just think there shoulde be much simpler solution for this issue.

---

### Post by LewisTM on 2012-06-26
Agreed.
To prevent the file for being overwritten, execute
```
sudo chattr +i ~/.config/xfce4/panel/xkb*
```
To unlock
```
sudo chattr -i ~/.config/xfce4/panel/xkb*
```
Far from user friendly but it works.

---

### Post by n00ne on 2012-06-27
not quite yet.
well I tried to lock the file but then I realized 
the settings are being modified after about 15 min even when the file is locked and without even restarting my computer.

so I completely removed the xfce4-xkb-plugin. this seems to work
and now I get the settings from the /etc/default/keyboard to load.

but for this only work on my laptop.
at my desktop even removing the plugin doesn't help
(maybe its because my laptop has a fresh install of xubuntu and my desktop is an upgrade from older ubuntu version)
so I guess there is some other conflict.
but how can I see what causing the problem ?
is this kind of thing might show up in the logs
and if so where and what should I look for ?

---

