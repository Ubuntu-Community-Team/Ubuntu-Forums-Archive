---
title: "can't start mplayer."
date: 2006-05-10
forum: General Help
---

### Post by newpants2003 on 2006-05-10
after clik the icon something flashed for half second and disppear, like nothing happened.
what  reason could possiable be? (i dont know what shuold i post for you to help me.)
it was fine yesterday, after i did something, dont remmember exactly...

---

### Post by hardXcore on 2006-05-10
you need to download the sub7 patch

---

### Post by newpants2003 on 2006-05-10
how?
sudo apt-get install sub
7 (like this?)

what does this to do with lunch mplayer?

---

### Post by nanotube on 2006-05-11
hi,
open up a terminal, and enter command "mplayer", and then post here with any error messages it may spit out.

---

### Post by newpants2003 on 2006-05-11
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu7 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP/XP-M Barton,Thorton (Family: 6,  Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


Usage:   mplayer [options] [url|path/]filename

Basic options: (complete list in the man page)
 -vo <drv[:dev]>  select video output driver & device ('-vo help' for a list)
 -ao <drv[:dev]>  select audio output driver & device ('-ao help' for a list)
 vcd://<trackno>   play (S)VCD (Super Video CD) track (raw device, no mount)
 dvd://<titleno>   play DVD title from device instead of plain file
 -alang/-slang    select DVD audio/subtitle language (by 2-char country code)
 -ss <timepos>    seek to given (seconds or hh:mm:ss) position
 -nosound         do not play sound
 -fs              fullscreen playback (or -vm, -zoom, details in the man page)
 -x <x> -y <y>    set display resolution (for use with -vm or -zoom)
 -sub <file>      specify subtitle file to use (also see -subfps, -subdelay)
 -playlist <file> specify playlist file
 -vid x -aid y    select video (x) and audio (y) stream to play
 -fps x -srate y  change video (x fps) and audio (y Hz) rate
 -pp <quality>    enable postprocessing filter (details in the man page)
 -framedrop       enable frame dropping (for slow machines)

Basic keys: (complete list in the man page, also check input.conf)
 <-  or  ->       seek backward/forward 10 seconds
 down or up       seek backward/forward  1 minute
 pgdown or pgup   seek backward/forward 10 minutes
 < or >           step backward/forward in playlist
 p or SPACE       pause movie (press any key to continue)
 q or ESC         stop playing and quit program
 + or -           adjust audio delay by +/- 0.1 second
 o                cycle OSD mode:  none / seekbar / seekbar + timer
 * or /           increase or decrease PCM volume
 x or z           adjust subtitle delay by +/- 0.1 second
 r or t           adjust subtitle position up/down, also see -vf expand

 * * * SEE THE MAN PAGE FOR DETAILS, FURTHER (ADVANCED) OPTIONS AND KEYS * * *

not only mplayer, beep player not working too. hope this my help
thanx.

---

### Post by nanotube on 2006-05-11
oh ok, now post what happens if you run command "gmplayer" (the mplayer is the commandline interface, gmplayer is the gui stuff.)

---

### Post by newpants2003 on 2006-05-12
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu7 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP/XP-M Barton,Thorton (Family: 6, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.



Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
[skin] file ( /usr/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).


looks it told me what the error is...
but i dont know how to fix it.
waiting for your help.
and also for vidoe players &#65288;ie: movie player&#65289;its really hard  when you try drag to control the  tempo(holp you understand what im talking about), is there a way to improve that?improve that?

---

### Post by nanotube on 2006-05-13
hmm, well, actually, when i run gmplayer, i get all the same stuff, the only difference being
```
[skin] file ( /usr/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).
```
so, your problem is that you have no skin for your gmplayer

can you post the output of command
```
ls -al /usr/share/mplayer/Skin/default/
```
just to see what you have in that directory?

the easiest way to fix it (if you indeed are missing the skin) is probably to reinstall the mplayer package. open up synaptic, search for "mplayer", find which mplayer package you have installed - and mark it for "complete removal", then hit apply button. now, mark it for installation, and again hit apply button.
that ought to fix it up.

or, you could of course just shove the skin into the location it is looking for it at. if you want, i can post a zipped archive of the entire contents of my skin dir for mplayer.

but anyway, first post the output of that ls command, so i can see what you have in there.

---

### Post by newpants2003 on 2006-05-14
thanx, i will try when i come back home.
i did remove and reinstall , using sudo apt-get remove mplayer
and remove using add/remove, but i didnt try synaptic. 

what about the smooth play control?

---

### Post by nanotube on 2006-05-14
[QUOTE=newpants2003]thanx, i will try when i come back home.
i did remove and reinstall , using sudo apt-get remove mplayer
and remove using add/remove, but i didnt try synaptic. 

what about the smooth play control?[/QUOTE]
i didn't understand what you are talking about with the play control thing... explain more clearly? :)

---

### Post by newpants2003 on 2006-05-14
or may shuold call it time control?

---

### Post by nanotube on 2006-05-14
so you mean you want to scroll around in the video?

---

### Post by newpants2003 on 2006-05-14
yes, i think that is what im taking about. very very hard  control compare to Media plater in windows,
i searched 'mplayer' on synaptic, only thing installed is the mplaye-skins. is that mean i dont have mplayer itself? if yes, which one shuold i install? there are a lot on the list.

---

### Post by nanotube on 2006-05-15
well, if you have a newer intel cpu, use mplayer-586 (pentium 2 and above), if you have an amd cpu, use mplayer-k6, and if you have a Really old cpu, use mplayer-386. 
so, based on these criteria, pick one and install it. :)

---

### Post by bluevoodoo1 on 2006-05-15
I had the same problem regarding the skin, reinstalling "mplayer-skins" fixed it!

---

