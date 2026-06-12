---
title: "What's the deal with Compiz in 12.04?"
date: 2012-07-14
forum: General Help
---

### Post by Triblaze on 2012-07-14
This is a rather general question, just looking for some information.  Compiz still seems to be used in 12.04 and a lot of places talk about installing ccsm and modifications you can do with it (I installed it as soon as I upgraded to 12.04 and made a few tweaks). But I've also been hearing some comments here or there that compiz can be dangerous to use and cause crashes, and indeed a few tweaks I made caused crashes. I worked these out and haven't touched compiz since.

I loved all the compiz effects in 10.10 (gnome), and they were all really smooth. However, in 12.04, there seem to be graphical hiccups everywhere. The only noticeable compiz feature I have on is workspace switching, and in 10.10 watching the windows slide in from other workspaces was very smooth. Now on the same computer, there are often little hiccups, windows kind of flicker at times when changing or flash. It's not very smooth, and seems to have a pretty low framerate too.

In short, what's the deal with compiz? Should I use it? Should I not? If I do, are there things I should avoid? And is it supposed to be laggier than previous releases?

Also, yesterday I noticed compiz was eating up 12-24% of my CPU while I wasn't doing anything. Normal?

---

### Post by Futant on 2012-07-15
Not had any problems with ccsm myself, and I don't know about the lagging, but a lot of people recommend Ubuntu Tweak and MyUnity, both of which are easy to use and have lots of tweaking options without causing crashes. I don't really use ccsm anymore and tend to use Tweak mostly.

---

### Post by mcduck on 2012-07-15
Compiz is working just as fine as before, any graphical issues you might have would be related to your graphics card and it's drivers, not Compiz itself (it requires a working GPU acceleration and if the drivers are not up to the task things can be less than perfect.)

When people are saying that "using Compiz is dangerous", they would actually mean that *tweaking Compiz settings with CompizConfig Settings Manager* can result in problems. Using Compiz is just fine, youa re suing it by default anyway, as Unity desktop is just a Compiz plugin...

And even tweaking the settings is fine, you just need to make sure you actually read any warning messages it might give you about conflicting plugins or keyboard shortcuts, and make a reasonable decision which plugin to enable in case that happens. Some plugins can have options and default shortcuts that conflict with the Unity desktop, so blindly clicking "OK" in any warning message might result in Unity plugin getting disabled to enable some other feature instead. (even in that case simply running "unity --reset" in a terminal should return you to sane Compiz settings that allow Unity to work).

---

### Post by Anzan on 2012-07-15
If you're going to use Unity in 12.04 then Compiz is the WM and you're stuck with it.

If you use Xubuntu or Lubuntu or Kubuntu or some other configuration of WMs or DE then you won't be bothered by its lagginess, resource gobbling, crashes, or failure to add window "decorations" like the close button.

---

### Post by elliotn on 2012-07-15
I use ccsm too, Ubuntu must find or come out with something that resembles compiz thus I will always use compiz, yes

---

### Post by Frogs Hair on 2012-07-15
I don't use many effects , but did enable some just to see if Compiz was still working on 12.04 . I didn't have any problems as long as I disabled the Unity plugin prior to making changes. After adding the desired effects I enabled the Unity plugin again.

Some of the video tutorials I viewed suggested dragging a terminal  shortcut to the desktop before starting for resetting Unity if there are are any problems.

---

