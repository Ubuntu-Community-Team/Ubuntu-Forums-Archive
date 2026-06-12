---
title: "Backlight sometimes turns off..."
date: 2012-08-28
forum: General Help
---

### Post by Stonecold1995 on 2012-08-28
I'm using Kubuntu 12.04, and sometimes the screen will turn off after I close the lid and open it again.  This is very annoying because sometimes I'll leave my computer on all night with important work open and I forget to save, and then I wake up and open the lid and the screen is black...  If I press control+alt+F1 to get to tty1's terminal, the screen turns on and works for *that*, but when I press control+alt+F7 the screen turns off (I see the cursor their for a split second before the screen turns off).  And I don't mean the screen turns black, but the backlight itself turns off.  If I go to tty1's terminal and kill Xorg, then I'll get into the login screen and it works again, but I don't want a *new* session, I want to be able to resume *old* one.  Is there a way to do this without starting a new session or rebooting my computer?

I tried things like restarting plasma-desktop, using "xset dpms force off; sleep 5; xset dpms force on" and then quickly pressing control+alt+F7 in hopes that "xset dpms force on" would run when I'm in tty7, but none of that worked...

I'm writting this all on elinks btw.

---

### Post by Stonecold1995 on 2012-09-01
Anyone?

---

### Post by Stonecold1995 on 2012-09-09
Recently I've also had a one-time similar problem that may be related to this.  I started up the game Touhou Project which tried to re-size the screen like normal so it could fit, but it seemed to only zoom in (so there were still a total of 1920x1080 pixels on the desktop, but the resolution itself was only 800x600, cutting off the majority of the screen).  Normally, Touhou Project doesn't have this issue.  When I closed the game, it didn't re-size the screen back, so I had to go to System Settings>Display and Monitor and tried to set it back to 1920x1080.  When I pressed Apply though, it went to the correct resolution for less than a second then the screen turned off just like with my original problem!  The screen turned on though when I pressed Escape to revert the changes and the resolution lowered again...  All other resolutions worked (from 640x480 to 1680x1050), but every time I tried my normal resolution, it works for a half-second, but the backlight turns off.  And as with my first problem, if I go to tty1, the backlight turns back on for the login screen, but as soon as I go back to tty7 the screen works for a split second but then turns off.  Weirder still, if I select the screen rotation to Upside-Down it works with a 1920x1080 resolution, but not if it's right-side up!  I ended up needing to reboot to fix the problem (killing Xorg also works, but I just rebooted this time).

Here's the output of "xset -q" (after I rebooted):
```
alex@kubuntu:~$ xset -q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    on     02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  387    repeat rate:  25
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  20/10    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,built-ins
DPMS (Energy Star):
  Standby: 21600    Suspend: 32400    Off: 43200
  DPMS is Enabled
  Monitor is On
```

I also tried turning off Energy Star by using "xset -dpms", but it didn't solve the problem.

The issue with the resolution not working was a one time thing, but I'm mentioning it because it may be related to my primary problem.  Can someone help me get more information on this?  It never use to happen, so I know my laptop's hardware is compatible (hell, even the fingerprint reader works, so I don't really think the issue is driver incompatibility), but it's happening so often now that, if I leave my laptop on overnight, there's a 70% chance that this problem occurs (and I usually leave my laptop on overnight to run Folding@home, so it's quite frustrating when I have to reboot often and my uptime rarely exceeds three days).

---

### Post by bra|10n on 2012-09-09
You could look here...

[IMG]http://i.imgur.com/smN3d.png[/IMG]

---

### Post by Stonecold1995 on 2012-09-09
I've looked through all the settings, and they're all normal as far as I can tell.
[IMG]http://www.pictureshack.us/images/7212_systemsettings.png[/IMG]

---

### Post by bra|10n on 2012-09-09
German -> translation = (-/+) English

Uncheck "Never prevent an action on lid close". 
If you are doubtful do NOT hover for the tooltip to further explain this...
A bug report was submitted for this sometime ago.

---

