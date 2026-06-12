---
title: "Can't stop suspend - screen turns off"
date: 2011-11-08
forum: General Help
---

### Post by Feelkarma on 2011-11-08
Hi all,
Just installed 11.10 and it seems like an endless quest, every time I jump through a loop there's another one.
Anyway, I have installed classic desktop and disabled suspend : system settings > screen > turn off after: never.
I have also disabled suspend in system settings > power > suspend when inactive for : don't suspend.
Nevertheless, the screen keeps on turning off every ten minutes, even with option 'disable screensaver' in VLC.

This is weird, any idea why? 

I had installed xscreensaver but uninstalled it.

Many thanks in advance

My config (64bit)
Dual boot Windows XP / Ubuntu
M/B: Asus M3N H HDMI with Phenom CPU
2gb Kingston PC8500 Memory
Pioneer DVD writer
Samsung 500 gb HD

---

### Post by glennbates on 2011-11-08
I have the same problem.  You would think "disable" means "disable".

---

### Post by jmacx81 on 2011-11-08
I also have installed xscreensaver and am about to give up on it. It seems like the screensaver that comes installed (or lack of one) doesn't work great and xscreensaver doesn't seem to be much better of an option.

---

### Post by deserthowler on 2011-11-08
I totally disable suspend and hibernate with ever install of a Debian based distro going to 
```
/usr/share/polkit-1/actions/org.freedesktop.upower.policy
```
and changing every [COLOR="Red"]yes[/COLOR] to [COLOR="Red"]no[/COLOR].

Earl

---

### Post by Feelkarma on 2011-11-09
Thank you, I will try tonight. This is another example of how you have to jump through so many loops just to do basic things, like the alt+clic that drove me crazy for a while, or the rather complex process of creating shortcuts on the desktop.
I've never used the terminal and google as much as since installing 11.10.
Oh, and my wife has threatened to buy a Mac :shock:

---

### Post by Feelkarma on 2011-11-09
It didn't work unfortunately. It seems other people are having the same problem and it appears to be specific to VLC in 11.10 (i.e. the screen does not seem to be going blank when VLC isn't running - which is quite ironical as the only time I don't want my screen going blank is when I actually watch a movie).

This is driving me nuts, and I can't get any surround sound with any other software than VLC so I'm stuck with it... :(

---

### Post by Feelkarma on 2011-11-09
Ok, it seems like I have found the solution, one of those two commands (or both) in the terminal which I found on the net did the trick, credits to original posters :

```
sudo chmod -x /usr/lib/gnome-screensaver
```or 

```
xset -dpms;xset s off
```Thanks to all!

---

### Post by Feelkarma on 2011-11-15
Marked this as unsolved again because I cannot figure out any way to make this work at startup - i.e. I have to open terminal and enter the code at the beginning of each session.

Is there a way to do this ? The actual code that is needed is:

```
xset -dpms;xset s off
```

I tried having this as a script at startup but no luck (i.e. it doesn't stop the screen from suspending after 10 min).

Is anyone else having this problem or did I do something wrong? It just seems so improbable that screen suspend after 10 min would be imposed.

Thanks

---

### Post by stinkeye on 2011-11-15
```
xset -q
```
Will show you if you are using DPMS (Energy Star)


If you just put 
```
xset -dpms
```
into startup applications it should stop the screen blanking every 10 mins.
This setting is separate from the screensaver.

The screensaver should be controlled by apps that have a screensaver off setting
or just set it in the screen app.

---

### Post by Feelkarma on 2011-11-15
Thanks Stinkeye,
the xset -q command gives :

```
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  33
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  600    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Disabled

```
I have tried putting the xset -dpms at startup but no luck (as it does not resolve the problem unless I actually open the terminal and key it in).

Isn't there a settings file that can be modified?

Ok, that's not a major issue but it would be goodto solve it... :)

---

### Post by stinkeye on 2011-11-15
> **Feelkarma said:**
> Thanks Stinkeye,
the xset -q command gives :

```
Screen saver:
prefer blanking: yes  allow exposures: yes
timeout: 600  cycle:600
```

I have tried putting the xset -dpms at startup but no luck (as it does not resolve the problem unless I actually open the terminal and key it in).

Isn't there a settings file that can be modified?

Ok, that's not a major issue but it would be goodto solve it... :)

Do you see this at the bottom with the **xset -q** command
```
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

```

---

### Post by stinkeye on 2011-11-15
Not that I know of.
Try using a bash script as the startup command.Remember to make it executable.
```
#!/bin/bash
xset -dpms

```

If I use either way, after log out/in 
xset -q
gives me
**DPMS is Disabled**

---

### Post by Feelkarma on 2011-11-15
Thanks, I tried but it still doesn't work (I put this in xset.sh in my home directory and made it executable via right click).

What is weird is that this never happened before updating to 11.10, I find it strange that no one seems to be having the same problem.

---

### Post by stinkeye on 2011-11-15
What's weird is the **xset -dpms** not working in startup applications.
I've always had the screen blanking.
I've used this in the the last 4 releases and now on 11.10 and has always worked.

Could try putting this in ```
~/.config/autostart
```
Save in gedit as **xset.desktop** (doesn't need to be executable)
```
[Desktop Entry]
Type=Application
Exec=xset -dpms
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_AU]=xset
Name=xset
Comment[en_AU]=
Comment=
```

---

### Post by Feelkarma on 2011-11-16
It eventually worked by adding xset s off to the script and restarting.
Many thanks again for the help!

---

### Post by joeqpublicus on 2011-11-17
I'm having the exact same problem a total noob here so please can you guys simplify what you guys did so I can do it on my system fresh install 11.10.

---

### Post by stinkeye on 2011-11-17
> **joeqpublicus said:**
> I'm having the exact same problem a total noob here so please can you guys simplify what you guys did so I can do it on my system fresh install 11.10.

What works for me is what I put in post #9.
Startup applications is in the logout icon on the top right.
Hit the add button
and just copy and paste
```
xset -dpms
```
in the command box as shown in the pic.

The screensaver will still function per your settings...screensaver settings are controlled by the **screen** application. 
**xset -dpms** stops the monitor turning off when idle for 10 mins.

---

### Post by joeqpublicus on 2011-11-18
> **stinkeye said:**
> What works for me is what I put in post #9.
Startup applications is in the logout icon on the top right.
Hit the add button
and just copy and paste
```
xset -dpms
```in the command box as shown in the pic.

The screensaver will still function per your settings...screensaver settings are controlled by the **screen** application. 
**xset -dpms** stops the monitor turning off when idle for 10 mins.



Sorry Stinkeye did exactly what you said and still the same problem persists every 10 minutes my screen goes black even though all my settings are placed to never do that both in power and screen lock.

---

### Post by stinkeye on 2011-11-18
> **joeqpublicus said:**
> Sorry Stinkeye did exactly what you said and still the same problem persists every 10 minutes my screen goes black even though all my settings are placed to never do that both in power and screen lock.

What does this in terninal give you 
```
xset -q
```


eg my last 3 lines give
```
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is **Disabled**
```


Other alternatve is to open gedit and save this in your home folder as 
**dpms-off**
```
#!/bin/bash
xset -dpms
xset s off
```
Right click on the saved file
Properties > permissions
and mark **Execute **

Then right click on the file and copy.
Open startup applications and paste the file copy as the command. (See pic)

Log out/in and in the terminal run 
```
xset -q
```
to check if dpms is disabled.

---

### Post by Feelkarma on 2011-11-19
Sorry, had to be offline for a day, the last instruction did it for me (thanks stinkeye!), it's quite clear I think, did it work? Need more detailed help?
One thing: not obvious is an understatement, to find your startup application you need to go to "other" under the application menu (I'm back to classic, Unity just doesn't work for me).

---

### Post by stinkeye on 2011-11-19
> **Feelkarma said:**
> Sorry, had to be offline for a day, the last instruction did it for me (thanks stinkeye!), it's quite clear I think, did it work? Need more detailed help?
One thing: not obvious is an understatement, to find your startup application you need to go to "other" under the application menu (I'm back to classic, Unity just doesn't work for me).
That"s why I **like** Unity.
Type in start and there it is.
Anyway glad it worked.
Bye.

---

