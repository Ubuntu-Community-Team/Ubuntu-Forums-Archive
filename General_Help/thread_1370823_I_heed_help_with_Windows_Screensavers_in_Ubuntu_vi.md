---
title: "I heed help with Windows Screensavers in Ubuntu via Wine"
date: 2010-01-02
forum: General Help
---

### Post by commodore256 on 2010-01-02
I can't figure out how to get my windows screensaver to play nice with linux.

Here's the screensaver that I wanna run: [http://www.3planesoft.com/clock-screensavers/mechanical-clock-3d-screensaver/](http://www.3planesoft.com/clock-screensavers/mechanical-clock-3d-screensaver/) (very steampunk)

I can only run it fine from the terminal, but, I don't know of any way to use xscreensaver as a timer and tell it "wine ~/.wine/drive_c/windows/system32/Mechanical_Clock_3D_Screensaver.scr /s" or "mplayer -fs ~/rickroll.mp4" or something.

I know how to get the starwars text to work by having it read a text file, but that's about it.

There's gotta be an easy way to do this, I'be spent 2 hours searching for this and no straight answer...

---

### Post by schievelbein on 2011-02-27
I would also like to run these screensavers.
How were you able to get them to run from the terminal?

---

### Post by Mark Phelps on 2011-02-28
Wine wasn't designed to emulate Windows in Ubuntu.  Instead, it was designed to provide a way to run SOME Windows programs by replacing default system DLLs (ones that do Windows OS calls) with other DLLs (ones that do Linux OS calls).

You could try checking in the Wine subforum to see if folks there have any suggestions.

But given the difficulty of even getting Linux screensavers to work, I doubt you'll succeed with the Windows screensavers.

---

