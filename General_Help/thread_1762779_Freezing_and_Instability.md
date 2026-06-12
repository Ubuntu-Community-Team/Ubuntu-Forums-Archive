---
title: "Freezing and Instability"
date: 2011-05-19
forum: General Help
---

### Post by W-Unit on 2011-05-19
Hi there,

First off, let me preface this by saying that I am, for the most part, a noob when it comes to *nix. I am quite knowledgeable when it comes to hardware (A+ certified) and Windows, but I really only know the basics of Linux. Thus, dumbed-down, simple instructions would be greatly appreciated :)

I am running Xubuntu 10.14 (32-bit) on quite an old PC that I intend to turn into sort of a media center. Not a media SERVER; I basically just want to hook it up to my TV and use it to watch Hulu, Netflix, etc. It's a totally fresh install - not running a dual boot or anything like that.

The PC was manufactured by eMachines and was probably purchased somewhere around '04-'05. It has an AMD Athlon 64 3400+ and 1GB of memory. The GPU and NIC are both integrated on the mobo, as is the audio controller. It ran about as smooth as sandpaper on WinXP and consequently has spent most of its life to date sitting in the garage.

Everything pretty much works fine running Xubuntu, except for one major issue. It seems that it just can't go for more than ~4 hours of uptime without freezing up or crashing. And by "freezing up," I do mean the "real" kind, where you can't move the mouse cursor, can't press CTRL+ALT+F1 to get the console, etc. 

The "crash" as I called it has only happened once, and consisted of me returning to the PC after leaving it running for a while to find that it was stuck on a console-style window. Kinda reminded me of a BSOD, if *nix had BSODs. Anyways, it didn't respond to any keystrokes or anything, and didn't appear to be doing any work, so I presume it was frozen up.

The freezing does seem more likely to occur when there's lots going on, however it has also occurred several times where the PC is totally idle, showing the screensaver.

Thank you for your time and any help you can provide! :)

---

### Post by r-senior on 2011-05-19
First thing I'd do with a machine of that age (especially one that's been run a lot), is open up the case and see if it's lined with dust, check the fans and vents, make sure the cards and cables are seated properly, etc.

If that's OK, try booting off a live USB or CD and run a memory check from the opening menu that comes up.

---

### Post by 3Miro on 2011-05-19
Does Netflix even run on Linux?

What exactly is your video card?

Hulu is flash based and Adobe has made an exceptionally bad job with Flash on Linux. I have had crashes on maximize/minimize of YouTube videos on some video cards.

My money here is on the video card. Integrated video card from 04-05 probably doesn't have very good drivers for Linux. If memory check doesn't return errors, you can try switching the video card to some cheap low profile Nvidia.

---

