---
title: "MultiMonitor Different Desktops"
date: 2010-06-29
forum: General Help
---

### Post by sdwinder on 2010-06-29
I tried to install ubuntu the other day using WUBI because I wanted to test out a couple things.

I heard about this magical option with dual monitors (which i use with windows 7) where, not only could ubuntu use both monitors, but that it would actually create 2 seperate xserver desktops, one for each monitor so they would actually work independently from eachother, (no extension display, and not cloned display). I had a couple questions about this.

1. Can it be done with an 8800gt nvidia card?
2. Can it be done period?
3. How is it done? I tried searching for this option under the   nvidia drivers and resolution/display options and could not get it working.
4. If this does in fact work, is it possible to do this with multiple monitors, and not just 2, like for example...hook up like 10 monitors and have each of them act independently.
5. Can i hook in multiple sets of keyboard/mouse and have them work in a certain assigned x server/ monitor, thereby creating multiple individual environments for users using only 1 single actual computer.....you see where Im going with this?

---

### Post by sdwinder on 2010-06-29
for the sake of clarity, I intend on running either a 3 monitors/desktop or a 4 monitor/desktop configuration where each monitor would serve as its own seperate entity and could run its own stuff (its own xserver).

I realize this may require an SLI setup with geforce cards and im ok with that, just wondering if its doable.

---

### Post by burton247 on 2010-06-29
It can be done with any card I thought. It should just be an option in the settings. Deffo there for my ATI card, can't really help you as you have an nvidia card :S

Don't see why It wouldn't work for more than 2 monitors, but I can't test that either.

And the keyboard thing, I have no idea!

Sorry I can't be of more use

---

### Post by sdwinder on 2010-06-29
What is the option called for the ati card?

---

### Post by burton247 on 2010-06-29
My options are:
Display disabled
Single desktop display (multi-desktop)
cloned display from display(s) 1
Multi-desktop with display(s) 1

The option you want (I think) is:
Single desktop display (multi-desktop)

---

### Post by sdwinder on 2010-06-29
Thanks, Ill try to mess with it, quick question though, since the monitors are in fact 2 separate entities, how do the window transitions and mouse keyboard transitions work between monitors? is it the same thing where you just drag them across?

---

### Post by stderr on 2010-06-29
My experience is with nVIDIA.

2 monitors was no problem - I could run as separate X screens, with Xinerama or TwinView if I recall correctly. Not all setups worked as well as one another (tbh there were small niggles with all), but generally everything was fine. 

3+ monitors was tougher. It seems to me that running _separate X screens_ is almost always absolutely fine, the ***only*** problem being that there is **no way at all** to move open windows between X screens (monitors). 

(full) _Xinerama_ was probably the best, with the ability to drag windows across all monitors, correct maximisation by default, etc, however in this setup I was unable to setup Compiz and had to run Metacity. Whilst it may possibly be possible to run Compiz under Xinerama, trust me, it certainly isn't easy, and not for a lack of trying, I still have no idea how it could be achieved. Also, fullscreen games never displayed correctly under this setup, and I was unable to fix this.

Finally, there's _nVIDIA TwinView_, but you can only run up to 2 monitors in this setup. This works well - compiz works, fullscreen games work (unlike my experience with Xinerama), dragging works, and with a little configuration maximising works too (although I couldn't find a way to prevent my panels stretching across both monitors). To support my third monitor, I ran that as a separate X screen, which also enjoyed Compiz support, but naturally you **cannot** drag (or otherwise switch) open windows between the TwinView setup and the other X screen.

I would also add that without Compiz, TwinView+Xscreen would not have been usable. However, there are other consequences to using Compiz instead of Metacity, such as slightly reduced GUI stability, and in my experience, far greater video tearing.

In my experience, it was rather a case of 6 of one, and half a dozen of the other. In the end I stuck with TwinView and a separate X screen, but it really depends on your setup and what you intend to use each screen for. Since my 24" wide is used almost exclusively for videos, it wasn't that problematic to use it as a separate X screen, but in some cases the dragging limitation is intensely frustrating.

---

### Post by burton247 on 2010-06-30
I forgot about that maximization rubbish...

I don't like have a separate x on each screen, I don't see the point. I use Xmonad as a WM and by default I can have a different workspace per screen, no maximization issues, move stuff between screens fine. Only annoying thing is the black space above my smaller monitor :(

---

