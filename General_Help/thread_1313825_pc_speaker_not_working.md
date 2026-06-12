---
title: "pc speaker not working"
date: 2009-11-04
forum: General Help
---

### Post by hossdozero on 2009-11-04
after upgrading to karmic,my pc speaker has stopped beeping when I use the terminal. Does anybody know how to enable it?

---

### Post by hossdozero on 2009-11-04
just tried some more trouble shooting.

I turned compiz off and was able to get system alert sounds, but still no pc speaker. 

when running compiz, alert sounds do not work whatsoever.

So, although I would prefer to have a system beep, If anybody knows how to get at least the system alert sounds working with compiz, your help would be greatly appreciated.

---

### Post by hossdozero on 2009-11-04
bump

---

### Post by P4man on 2009-11-04
most people ask the opposite lol.
Check ```
/etc/modprobe.d/blacklist.conf 
```
See if ```
pcskpr
``` is blacklisted there. If it is, connent that line out if you really enjoy those beeps :)

---

### Post by renkinjutsu on 2009-11-04
check to see if you have the module loaded
```
lsmod|grep pcspkr
```
if it's not loaded, then ```
sudo modprobe pcspkr
```

for a permanent fix (i'm not sure if this is the correct way, but here goes)

```
sudo nano /etc/initramfs-tools/modules
```
and add pcspkr to the bottom

if you don't have this file, you may have to ```
sudo aptitude install initramfs-tools
```

after adding pcspkr to the file, just ```
sudo update-initramfs -u -t -k all
```

---

### Post by grandtoubab on 2009-11-04
first try 
```

alsamixer
```

and check the level

---

### Post by hossdozero on 2009-11-04
It was blacklisted.

I commented it out of the blacklist ran the modprobe
and added the command to modules list. then ran the update

I'm still not getting alerts under compiz BUT, the pc speaker does work when i run the beep program now. so we have gotten at least that far.

> most people ask the opposite lol.

call me old fashioned.O:)

---

### Post by alter1 on 2009-11-04
I have the same problem. I followed the stated steps. 
The module is correctly loaded.
The "beep" command works ok (uses the pc speaker)
But the terminal still does not use the pc-speaker.
Btw the following command
printf "\a" 
does not use the speaker.

I'm using metacity, not compiz.

I find that using the sound system instead of the pc-speaker is very annoying
(it lags, it doesn't repeat, its volume depends on the system volume).

In the university where I work, none of the machines in the student's classes have loudspeakers.
So this can be quite a problem...

---

### Post by hossdozero on 2009-11-05
also, even though I added the "pcspkr" line to the modules list, the module doesn't load on startup.

---

### Post by alter1 on 2009-11-05
Well, I've been looking into it but still have no solutions.
It seems to be a gnome or window manager problem.
Disabling event sounds removes the sound alltogether, but I haven't managed to get the beep back.

My "beep" command works (through the pc-speaker), the pcspkr module is enabled.

---

### Post by alter1 on 2009-11-06
I've tried a lot of stuff... checked for any bell related options with gconf-editor ... nothing works. 
I can't enable the beep in gnome-terminal
(though the beep command works)

Any ideas?

---

### Post by alter1 on 2009-11-07
bump

---

### Post by P4man on 2009-11-07
have you tried a different terminal app?

---

### Post by alter1 on 2009-11-07
I tested xterm also : same problem

Actually I've just made a little progress:
There's a lot on this here:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/301174](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/301174)

The problem comes from pulse audio that has a module called "module-x11-bell" to
"playback a sound file in place of the X11 bell beep."
(apt-cache show pulseaudio-module-x11)

I don't know how to configure pulse audio not to use this module.
I tried:
pactl unload-module module-x11-bell
but it doesn't work.

The bell line is already commented in :
/etc/pulse/default.pa

One thing that does work is :
pulseaudio -k
That restarts pulse. During the few seconds pulse is down, the beep works.
I would like to find a good clean long term solution.

---

### Post by P4man on 2009-11-07
sounds like you're getting close. actually, wouldnt you have to *enable* to bell module rather than commenting it out?

---

### Post by alter1 on 2009-11-07
EDIT: sorry, actually, the pc-speaker like sound was coming through the loudspeakers, not from the pc-speaker.

Yeeeeeessss!!!!! That works!!! Thanks!
After so many hours of trying ... the good old beep is back again! ;)

You were right, enabling it was the right thing (I got it backwards).

So finally, here are the steps I took to get the beep back in karmic (9.10):

Get the blacklisted kernel module back:
In /etc/modprobe.d/blacklist.conf comment the following line:
#blacklist pcspkr

Tell pulse audio to load the x11-bell:
In /etc/pulse/default.pa uncomment the following line:
load-module module-x11-bell sample=bell-windowing-system

Then restart everything.

If you have any trouble:
make sure the pcspkr module is loaded: the following command should display something
lsmod  | grep pcsp

---

### Post by hossdozero on 2009-11-07
terminal beeps are still not working for me, with or without using compiz.

And something weird is going on with the module, 

```
lsmod | grep pcspkr
```

states that the module is loaded at start up, but even the beep command won't work without first stopping then restarting the module.

---

### Post by alter1 on 2009-11-08
Sorry for my previous posts. :mad:
Actually the steps I followed simulate a pc-speaker-like beep on the loud-speakers. 

But my pc-speaker is really not working at all. 
Not even with the beep command.
I confused the sounds as they really sound like a pc speaker beep...

So, finally there was no progress here at all.

---

### Post by markus.s on 2009-11-16
hi,

I had the same problem
especially I missed the ping sound (ping -a) in gnome

modprobe pcspkr
xset b on

helped me!

rgds

---

### Post by hossdozero on 2009-11-16
It worked! 

OK, how would I go about running the xset command at startup?

---

### Post by markus.s on 2009-11-16
depends on your desktop-manager

independent:
~/.profile
/etc/rc.local

---

### Post by P4man on 2009-11-16
> **hossdozero said:**
> It worked! 

OK, how would I go about running the xset command at startup?

If you're using gnome I guess you could just add it to your session. System > preferences > startup applications

---

### Post by hossdozero on 2009-11-17
> **P4man said:**
> If you're using gnome I guess you could just add it to your session. System > preferences > startup applications

This worked. thanks everyone.

---

### Post by Jussl on 2009-11-23
Didn't help me... 
Only solution I have found is:
```

rmmod pcspkr
modprobe pcspkr

```[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/398161](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/398161)

But this requires root privileges.
Anyone knows where I should put these commands to run them as root at start up?

---

### Post by Snoop Kakapo on 2009-12-01
just do this steps:

------------------------------------------------------------
in /etc/modprobe.d/blacklist.conf
#blacklist pcspkr
------------------------------------------------------------
in /etc/initramfs-tools/modules
pcspkr
------------------------------------------------------------
sudo update-initramfs -u -t -k all 
------------------------------------------------------------
and to System > Preferences > Startup Applications
xset b on 
------------------------------------------------------------
and RESTART
------------------------------------------------------------


cheers,
Snoop

---

### Post by Michael Knap on 2009-12-01
I too would like to see this issue fixed. I often run many calculations and applications. I like the audible bell to let me know something is up. I too can hear the bell with metacity, but not with compiz. 

A visual workaround is to enable some of compiz's possible settings. For instance under the wobble windows plugin, there is a shiver option with an icon featuring a speaker beside it. CHeck this to have the window producing a beep to shiver. I also use the tidal wave under water effects.

THese help, but I would prefer the audible beep. 
Again it works in metacity, but not with compiz. Do you have the same experience ?

---

### Post by Snoop Kakapo on 2009-12-02
so try add this:

------------------------------------------------------------
in /etc/rc.local script
rmmod pcspkr
modprobe pcspkr
------------------------------------------------------------

---

### Post by Snoop Kakapo on 2009-12-03
so here is final solution:

------------------------------------------------------------
in /etc/modprobe.d/blacklist.conf
#blacklist pcspkr
------------------------------------------------------------
in /etc/rc.local script
rmmod pcspkr
modprobe pcspkr
------------------------------------------------------------
and to System > Preferences > Startup Applications
xset b on
------------------------------------------------------------
and RESTART
------------------------------------------------------------

cheers,
Snoop

---

