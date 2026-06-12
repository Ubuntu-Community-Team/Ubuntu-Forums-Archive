---
title: "Upgrade to 10.10, no login screen"
date: 2010-12-16
forum: General Help
---

### Post by Mark_Lester on 2010-12-16
Hello folks.
So I went through the epic 4 hour upgrade from 10.04 this evening in the hope that I'd be able to use the mic on the logitech webcam pro 9000 I've just got.
Anyway, I get the purple Ubuntu screen with the 5 white to red dots, but then nothing more, it just sits there.
Alt-f4 gives me a login prompt, and I can login in, which is at least something.
Is there a way from there that I can go back at least to what I had, or even a magic command I can run from there to actually get into a gui ? 
It's a nice home made machine from a statndard build from Buildyourownpc.org if that helps, I can get you the deets if needed but it's been dandy till now. I zapped some X related stuff , xlib-utils I think, from within synaptec in order to get rid of some ciruclar deps that was blocking the upgrade if that explains anything. Though after 4 hours I'd have thought it would have healed up any of my vandalism.

Thanks in advance for any tips

---

### Post by Mark_Lester on 2010-12-17
last few lines in syslog say

--------

pulseaudio /etc/timidity not ours
failed to acquire autospawn log
...something about network driver
init failsafe-x terminated
-------

---

### Post by Mark_Lester on 2010-12-17
looks like I've really fouled this up, I seem to have lost xwindows
I re-installed
sudo apt-get install xwindows-system
and it got on with loads of stuff
I dont have the init failsafe-x terminated message now, but I still dont go through to a login screen

---

### Post by Mark_Lester on 2010-12-17
OK,
sudo apt-get install kubutnu-desktop

installed half the universe, and I get a log in, things are still in a bit of a mess, I'm in low res but I'm sure I can fix that eventually.

So the only useful feedback I can give is

1. I tried upgrading from 10.04 to 10.10
2. it whinged about a circular dependency so I removed xwindows-utils

---

### Post by Mark_Lester on 2010-12-17
so here I am, back in, but the only options I have on monitor size is 640:480 (4:3)
it says it's got the ATI FGLRX driver.

irritatingly, on startup, the purple intro screen is higher res than it used to be (Ubuntu and the 5 dots are smaller than they were before I left 10.04).

I appear to have a shed load of new software ready to go, ta very much, but this screen is barely usable :(.
 
looking for something else to apt-get ......

---

### Post by Mark_Lester on 2010-12-17
and finally

it seems to be an issue with having both the vga and the hdmi plugged in, i had issues before where I had to plug the hdmi in after I'd booted else it wouldnt work. I've got some half flashy graphics card with it.

also, my "purple screen" says mythbuntu of course, so along with my insane decision to remove X thinking it would heal up during the upgrade, that may have been another factor.

And my logitech now works, not sure now if that was a function of the upgrade as I now have the ubuntu desktop as I couldnt find the option on the menu's on xfce i think it was, but anyhow, everyone's a winner.

thanks for allowing me to moan on about my woes, and many thanks from the world at large to everyone chipping in and for the ocean of new stuff that's turned up with this upgrade. one evening on my wife's laptop and XP was more than enough ;).

---

