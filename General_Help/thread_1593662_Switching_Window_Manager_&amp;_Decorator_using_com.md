---
title: "Switching Window Manager &amp; Decorator using command line/shell script"
date: 2010-10-11
forum: General Help
---

### Post by bobwyajnr on 2010-10-11
Hi all,

[SIZE="2"]I am using Lucid 10.04 (x64) and luving it on my 4Ghz Core i7 rig! Finally managed to get a custom kernel (2.6.35.7) compiled and installed this morning (after 2 weeks of attempts). I have also managed (finally) to get the F@home GPU client to work with WINE and an old version of Nvidia CUDA... Also had a lot of success running games under WINE with the Steam Windows client (Bioshock, Stalker: Shadow of Chernobyl, HL2.0), etc.!! :popcorn:

I [COLOR="Yellow"]need[/COLOR]like to use Compiz... My dock and Windows look a bit naff without it running (no aero glass, dock has a black blob behind it - instead of being properly transparent). Problem is of course that Compiz does GPU offload. So when enabled it craps on my Steam games (running under WINE) and also my Folding@home GPU client brings my Compiz interface practically to a jerky, standstill...[/SIZE]


Anyway to actually get to my question... :guitar:
I use the Compiz Fusion tray icon to switch Window manager, switch decorator and then reload window manager (when switching from Emerald to GTK and visa-versa). I would like to know what actual commands the tray icon is running to perform these 3 steps (in both directions: Compiz-> GTK and GTK->Compiz)?!! This would allow me to write simple shell scripts to launch my Folding@home GPU client and Steam client that do the Window manager switch automagically.

Thanks for any help you guys can provide!!
Bob

---

### Post by VCoolio on 2010-10-11
"compiz --replace" and "metacity --replace" for starters.

---

### Post by bobwyajnr on 2010-10-11
> **VCoolio said:**
> "compiz --replace" and "metacity --replace" for starters.

Well as you can probably guess from my post I did get so far as to try out those to commands!!

Your post spurred me to investigate further and I managed to resolve my question myself! :lolflag:

I now see that one Window manager has a single active process at a time (Metacity or Compiz). Good old **ps** shows me the commands being run exactly (obvious really - should have tried this myself earlier):
**Compiz/Emerald active**
```

$ ps aux | grep compiz
compiz --sm-disable --ignore-desktop-hints ccp --indirect-rendering

```
**GTK/Metacity active**
```

$ ps aux | grep metacity
metacity --replace

```
Allowed me to see that these processes are run as my user (i.e. not root) and what switches were used. When I reload the Window manager, via the Compiz Fusion icon, the process ID changes. So obviously all it is doing is killing the Window Manager and relaunching a new process with the same command line switches!

The Windows decorator appears (Compiz=Emerald, Metacity=GTK) to switch automagically... Presumably if you had a different Compiz Windows Decorator installed say - then you could switch between them. But you can't run a Compiz Windows Decorator under Metacity and visa-versa.

---

