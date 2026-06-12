---
title: "Moniter resolution out of range with some apps"
date: 2010-05-18
forum: General Help
---

### Post by kahootbot on 2010-05-18
I've noticed when I execute some games/programs that go full screen my moniter gives the error "Moniter resolution out of range"

I'm thinking maybe it's showing that it can support a lower resolution but isn't or something. I've had this problem with commercial as well as free games like tuxmath, freedroidRPG, humble indie bundle, etc.

Any ideas?

also, is there a way to change the resolution from one of the avaliable command lines other than f7? I'm getting tired of ctrl-alt-f1 + sudo reboot..

---

### Post by pandanuma on 2010-07-16
I finally found the info you need on the freedroidRPG web page...
click info then documentation...
scroll down to screen resolution

freedroidPRG -r99 gives you a list of screen resolutions available

oddly enough, freedroidRPG --help, was very helpful too

basically, start in a terminal with:  freedroidRPG -w
this opens the game in a window, not fullscreen

If you are stuck in the screen of black death (screen out of range)
try arrowing down about 10 time and press enter...
that should blindly select the quit menu option

---

