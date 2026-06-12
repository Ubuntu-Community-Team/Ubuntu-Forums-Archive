---
title: "Ubuntu Crashing/freezing help"
date: 2009-12-02
forum: General Help
---

### Post by forrestno on 2009-12-02
Hey all, I have recently upgraded to 9.10 (64bit) and after about a week with no problems I ran into an issue with the computer freezing up, flashing/scrolling black and grey, my mouse and keyboard both stop working and eventually stopping all signals to my monitors.  It always seems to happen when I have a video playing from the web.  After it happens I have to power down my computer and have no use.  Here is a logs at the times of a crash.

Dec  1 23:53:39 nate-desktop kernel: [ 4908.532216] Xorg[1483]: segfault at 8 ip 00007fb897e5b10f sp 00007fff720d3f80 error 4 in ld-2.10.1.so[7fb897e4d000+1f000]
Dec  1 23:53:54 nate-desktop bonobo-activation-server (nate-3078): could not associate with desktop session: Failed to connect to socket /tmp/dbus-rwiXhzc2h3: Connection refused
Dec  1 23:54:02 nate-desktop kernel: Kernel logging (proc) stopped.

hopefully someone can make sense of that, I'm a relatively new user to ubuntu so I'm pretty lost.

EDIT: This happens randomly and I have no idea how to "trigger" it

---

### Post by scraghty604 on 2009-12-02
I have a 32 bit system and seem to have almost the same problem...Ran fine for about two weeks, Then all of a sudden it started doing it.  I believe it has something to do with recently installed plugins.

And its pissing me right the F*uck off sometimes i can go 5 mins sometime i can go 20 minutes by you know right when you think your good to go BAME freezes up.


I cant remember exactly what I recently installed but heres a shot
Downloadhelper Addon for firefox
ffmpeg
and a crap load of plugins

did you notice this problem after installing anything like that maybe we can narrow it down.

Nothign has to be running...I can boot up and it will crash not even 30 sec. later sometimes.

Also My wireless has acted up ever since as well  It will connect then on cue it will dis connect after about a minute then connect again on its own.  Never had that problem until the freezing thing started happing.

Can any of the Ubuntu geniuses maybe direct us to some file that would tell us what error is causing the crash. It has something to do with the system i think...its very random and only started after recently installed a bunch of stuff...problem being when downloading packages it automaticly adds other needed files to it to...so I have no clue were to even start by uninstalling.

---

### Post by twilight_zone on 2010-07-04
Hmm,

interesting comments....
Had the same problem after installation of Downloadhelper Addon
I played around on a parallel installation(separate diskdrive), so I didn't damage my working environment, but it showed me to be carefull with this addon. 

Try to describe what happened :
- tried to download a file with download helper
- suddenly system "hang" an Firefox disappeared from desktop
- I was not able to shutdown the system anymore
- tried to get another terminal to shutdown from there -> not able to login 

-> bad decision -> power down system

I've reinstalled Ubuntu several times on that "test drive" and could repeat the failure
always the system crashed and needed a (hard) power shutdown with the consequence of a damaged filesystem
I wasn't able to fix it, so I completely reinstalled Ubuntu...

I recommend NOT to use this ADDON !!
TZ

---

