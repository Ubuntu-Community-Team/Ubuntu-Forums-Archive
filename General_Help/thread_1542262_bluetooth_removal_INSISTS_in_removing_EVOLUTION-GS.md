---
title: "bluetooth removal INSISTS in removing EVOLUTION-GSTREAMER-XMMS etc ?????????????"
date: 2010-07-30
forum: General Help
---

### Post by Crisis13 on 2010-07-30
WHY does ubuntu remove evolution en g-streamer IF I REMOVE BLUETOOTH ???
My computer HAS NO BLUETOOTH and i DONT NEED IT

[IMG]http://home.hccnet.nl/c.born/bluetooth-DUMB.png[/IMG]

---

### Post by philinux on 2010-07-30
Crisis13,

The bluetooth packages amount to Kbs or maybe a couple of megs.

Just disable it in System>prefs>Startup apps.

---

### Post by Crisis13 on 2010-07-30
Thanks for your reply,
I removed the auto-start long ago

[IMG]http://home.hccnet.nl/c.born/Startup Applications Preferences.png[/IMG]

Kbs, do you mean Kilobytes or Key-bindings ??
There is no 'Kbs' as such installed in Synaptics.

---

### Post by ajgreeny on 2010-07-30
I think philinux simply meant that it takes up very little disk space, so may not be worth removing.

Incidentally I have removed a lot of the bluetooth applications, and did not see the attempted removal of all those things you speak of, except for a couple of the library files which wanted to remove several of the gnome desktop applications I needed.

All I have now is **libbluetooth3** and **libgnome-bluetooth7.**

Incidentally you can completely stop bluetooth running by installing BUM (**B**oot**U**p**M**anager) and running that.  It can also stop some other services that you may not need or want, but check them out first.

---

### Post by philinux on 2010-07-30
Kilobytes. The bluetooth stuff is quite a small package.

---

### Post by Crisis13 on 2010-07-30
Alright, i gonna try BUM.
And its not about the space BT takes but my system of 1,7 Ghz is constant at the 100%, with 2-3 clicks, so i have to clean my system.

If i continue with removing every thing, what might happen?
I wanted to uninstall evolution since i use thunderbird but then ubuntu wanted to UNinstall the whole ubuntu-desktop

Ubuntu is just like a pot off spagetti, easy to eat,
but you cant find the beginning nor the end...

So I dont MIND evolution and totem to be UNinstalled,
but what is left off ubuntu if i do so ???

---

### Post by arpanaut on 2010-07-30
If your CPU is running  100% there probably are other issues than what is installed on your system.
Only if a program or app. is running is it going to be using the CPU or RAM, otherwise it is just using up disk space, and for the most part very little of that especially on the huge disks available these days.

Something is using up your resources to see what that may be, open a terminal and enter 
```
top
```
this will show you what is using up your resources.

Just removing random packages that may or may not have anything to do with your issues can and probably will render your system useless.

Do some investigation and then then trouble shoot the pertinent problems.

Meh? My 2 cents.

---

### Post by ajgreeny on 2010-07-30
> **arpanaut said:**
> If your CPU is running  100% there probably are other issues than what is installed on your system.
Only if a program or app. is running is it going to be using the CPU or RAM, otherwise it is just using up disk space, and for the most part very little of that especially on the huge disks available these days.

Something is using up your resources to see what that may be, open a terminal and enter 
```
top
```this will show you what is using up your resources.

Just removing random packages that may or may not have anything to do with your issues can and probably will render your system useless.

Do some investigation and then then trouble shoot the pertinent problems.

Meh? My 2 cents.
+1
I totally agree with this.  A cpu at 100% means something is definitely wrong, if it stays at that level all the time.

---

### Post by Crisis13 on 2010-08-02
> **ajgreeny said:**
> +1
I totally agree with this.  A cpu at 100% means something is definitely wrong, if it stays at that level all the time.

Not all the time, fortunately.
But if I start youtube it migth get stuck easily, and i don't mean 5 pages at once.
With myspace i have the same overload. Just a stream takes the lot of my cpu, which still has a real 1.69 Gihz. I noticed Ubuntu does not realy check the max possibilitie of the hardware, it has general functioning code , based on the most common computers.
And a compaq evo p4 of 1.7 gihz might but just out off sight :(
I pitty it that the regular Linux INSTALL aint realy looking at the MAX off the hardware and THEN makes a decision WHICH kernel is apropiate for the specific machine.
Last year i got the message "by new hardware for your linux problem" severall times in FORUMS.
But that is BEYOND one off the primair rulez of LINUX, "fit IN THE computer".
My hardware is known for 8-10 years now.
I CHANGED 5 graphical cards JUST to have my 3d BACK IN 1 YEAR.
and ALL cards ARE IN GOOD CONDITION !!!!!!!!!!!(ati nvidia)
I dont mind LECAGY aslong as LINUX and THUS Ubuntu WANTS to use it as it is.

I understand Ubuntu is a compilation off programs , gathered in a "distribution" but if ubuntu IT SELF suggests to REMOVE to lot ,( the reason for this tread, please remember !!), then there is something very much done to much.
Perhaps there i will find the reason why my 1.7 GiHz computer easily overloads while its doing nothing special.

More and more IMAGES are just plunged in
" And NOW it works" for 99%
But what if your computer differs MORE than 1%?????

Then ubuntu has not a clue...

So 
IF
i UNinstall Evolution/bluetooth


WHY 
does
UBUNTU
REMOVE
the
UBUNTU-DESKTOP


THE BLOODY DESKTOP
(jail-time???)


PLEASE 
CAN SOME ONE
ANSWER
THIS
QUESTION??


meanwhile
enjoy
[http://www.worldofspectrum.org/infoseekplay.cgi?title=4+on+a+Row+v3.0c+%28compiled%29&pub=CrisiSofT&year=2005&id=0016718&game=/games/123/4OnARowV3.0c%28compiled%29.z80.zip&emu=3](http://www.worldofspectrum.org/infoseekplay.cgi?title=4+on+a+Row+v3.0c+%28compiled%29&pub=CrisiSofT&year=2005&id=0016718&game=/games/123/4OnARowV3.0c%28compiled%29.z80.zip&emu=3)

i wrote it my self,
4connect i mean,
not the java ZX-emulator

---

### Post by mcduck on 2010-08-02
> **Crisis13 said:**
> 
So 
IF
i UNinstall Evolution/bluetooth


WHY 
does
UBUNTU
REMOVE
the
UBUNTU-DESKTOP


THE BLOODY DESKTOP
(jail-time???)


PLEASE 
CAN SOME ONE
ANSWER
THIS
QUESTION??

It doesn't, and there's no need to shout.

"ubuntu-desktop" is an empty metapackage, that has all the things included in nthe default Ubuntu setup marked as it's dependencies, so installing that package will bring along everything you get on the defalt Ubuntu desktop.

On the other hand, no package depends on the "ubuntu-desktop", so uninstalling it won't uninstall anything else than the metapackage itself.

What you still need to consider is what happens if you start removing different libraries from the system, as many of the programs you ave installed might actually have featured that require those libraries, and therefore the programs may actually need you to have a certain bluetooth- or evolution-related library installed. For example Gnome-panel integrates with Evolution, providing easy access to calender events through clock applet. This means that the panel needs a certain Evolution library, and if you uninstall everything Evolution-related you end removing the panel as well.

Anyway, whatever you have installed on your system won't effect the actual problem you are having. Or, actually, 100% CPU use when viewing a flash video any heavy web sites. doesn't sound that strange at all. Flash is insanely heavy, and the Linux version is even worse than the Windows/OSX versions are.

---

