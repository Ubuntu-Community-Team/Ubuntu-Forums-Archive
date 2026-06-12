---
title: "boot sequence stuck on unreadably distorted X dialog, but I don't want X"
date: 2009-12-21
forum: General Help
---

### Post by TsarBomba on 2009-12-21
Out of seemingly nowhere, but probably after I did a [FONT=Courier New]apt-get update && apt-get upgrade[/FONT], my boot sequence no longer finishes.  It gets stuck on what I believe is some X-based gui dialog (not curses-based), but the screen is unreadably distorted (as if each horizontal row of pixels has been shifted by some different amount).

First of all, nothing X-based should happen at all.  I actually hate any gui-based login, splash screens, starting X when I don't have to, etc. (and here's a good reason why).  Therefore, I unstalled [FONT=Courier New]gdm[/FONT] (don't know why turning the service off didn't acomplish anything, like it does in Jaunty), and I use the [FONT=Courier New]nosplash[/FONT] boot option.  Usually I login at the console... what I'm used to calling runlevel 3 in other distros.

So, you might just be able to stop reading here and answer this: what could possibly be giving me this X-based gui when my normal boot sequence doesn't involve X at all?

When I hold the power button to reset, sometimes it actually displays correctly for a split-second before the system resets.  It looks like a dialog with a single OK.  Hitting enter (on a separate try, while it's messed up) apparently brings up another dialog.  No matter what I hit there (enter, tab, up-down, enter again, etc.) nothing happens, and I've yet to catch a split-second glimpse of what that one really looks like.  I can hit ctrl-alt-f* to get to other virtual consoles, but they're completely blank.

Furthermore, I can boot to single-user mode, run [FONT=Courier New]init 3[/FONT], and then login and [FONT=Courier New]startx[/FONT] as usual.  That works fine.  *Why is single-user mode and init 3 not equivalent to my normal boot sequence?!*

I've checked /var/log/messages and I don't see anything out of the ordinary.  If fact, the boot sequence looks just about done before it runs into the problem; everything essential is up and running.  I see that it drops in a /var/log/Xorg.failsafe.log file:

Here are the errors:
```
root@coronet:/var/log# cat Xorg.failsafe.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) config/hal: couldn't initialise context: unknown error (null)
```I don't anything about hal, other than the service is usually running.  Maybe it X needs it but it hasn't started here yet?

Here are the warnings:
```
root@coronet:/var/log# cat Xorg.failsafe.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(WW) VESA(0): Unable to estimate virtual size
(WW) VESA(0): No valid modes left. Trying less strict filter...
(WW) VESA(0): Unable to estimate virtual size
(WW) VESA(0): No valid modes left. Trying aggressive sync range...
(WW) VESA(0): Unable to estimate virtual size
```Well, that certianly sounds like my problem, but doesn't help.  **Again, X works fine when I start it myself with startx as I usually do.  I'm not really looking to solve these X errors, just fix whatever is now in my boot sequence that's attempting to start X in the first place.**

I'm running the very latest karmic.  By booting into my normal environment using the single-user, init 3 route, I've done [FONT=Courier New]apt-get update && apt-get upgrade && apt-get dist-upgrade[/FONT].  Nothing changed.  This is on an Asus Eee PC 1005HA.

Any help would be greatly appreciated.

Thanks in advance.

---

### Post by TsarBomba on 2009-12-21
When it's stuck on that scrambed dialog, and I switch to a different virtual console, which is blank, I can actually login.  Nothing ever appears on the screen, but I can type out [FONT=Courier New]ps axjf > ps.out[/FONT] and go read it later by booting single-user.  And here's the offender:

```
/bin/bash /etc/gdm/failsafeXServer
 \_ xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe -- /usr/bin/X -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log
     \_ /usr/bin/X :0 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log
     \_ /bin/bash /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe
         \_ zenity --warning --text <big><b>Ubuntu is running in low-graphics mode</b></big>\n\nThe following error was encountered.  You may need\nto update your configuration to solve this.\n\n(EE) Failed to load module "i810" (module does not exist, 0)
```So module i810 is the secondary problem here (the primary problem being why failsafeXServer is even starting in the first place).  But I see this error in my everyday Xorg.0.log, when everything works fine:

```
(II) LoadModule: "i810"
(WW) Warning, couldn't open module i810
(II) UnloadModule: "i810"
(EE) Failed to load module "i810" (module does not exist, 0)
```That's because it loads intel before that, and is apparently fine using it:

```
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
```(The hardware is: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03))

I must admit, I don't know what failsafeX is, but apparently it's not as failsafe as plain old X :)

And why is there an /etc/gdm when I uninstalled gdm?  Hmmm, I see it's owned by the x11-common package.  Anyways, gdm is definitely uninstalled:

```
root@coronet:~# dpkg -l | grep gdm
root@coronet:~# service gdm status
gdm: unrecognized service
```I don't want to get to sidetracked by this specific i810 issue, but I can easily tell that nothing in where I would normally look for X config names that driver:

```
root@coronet:/etc/X11# find . -type f | xargs grep i810
root@coronet:/etc/X11#
```But there's no xorg.conf like I'm used to (new bulletproof X, I guess, which IMHO is more of a PITA than before).  There's xorg.conf.failsafe, but it specified Driver "vesa".

Of course, maybe it's trying to start X to prompt me about some other problem that never even gets expressed, so fixing this is worth a shot.

But, again, if anyone knows how to get the behavior back to my non-X login environment, the way everything was working up until today, I wouldn't even have to think about this driver issue.

Thanks

---

