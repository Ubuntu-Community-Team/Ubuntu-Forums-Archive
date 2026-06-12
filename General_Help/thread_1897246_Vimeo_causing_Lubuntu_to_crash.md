---
title: "Vimeo causing Lubuntu to crash"
date: 2011-12-18
forum: General Help
---

### Post by Jargson on 2011-12-18
I'm starting to think it's a video card problem.  I installed Ubuntu on a computer with 512 MB of ram, 3200+ AMD Athlon 64 processor, ATI Radeon X200 IGP and after it installed successfully the entire screen besides the menu bar and the launcher bar was black, and although I could move my mouse around the blackness and click icons on the launcher and open them, they would be behind the blackness and unable for me to access them.  With the advice of this forum, I installed lubuntu instead, and it's working great so far. 

Except, when I try to play videos on Vimeo it turns the whole screen white and the computer freezes and I have to do a hard reset of the computer.  Any fix known for this?

---

### Post by SteveDee on 2011-12-19
> **Jargson said:**
> ...Except, when I try to play videos on Vimeo it turns the whole screen white and the computer freezes and I have to do a hard reset of the computer...

I suggest you try other players like Gnome Mplayer (should already be installed) and VLC. This may show if its a general graphics/video problem, or player specific.

If you launch a player from the terminal you may also see some diagnostic info. Example in a LXTerminal window type:-
```

gnome-mplayer

```

In Gnome Mplayer you could also try changing the video output setting (menu Edit > Preferences > Player > Video Output). On at least one of my machines I have to select "x11" to avoid problems.

---

