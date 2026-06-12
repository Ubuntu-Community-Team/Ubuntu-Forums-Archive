---
title: "tiny text in programs"
date: 2011-04-30
forum: General Help
---

### Post by DanBender on 2011-04-30
I'm running Mythbuntu 10.10 64-bit and have noticed an issue with the size of the text in some of the programs (VLC, Okular, and Oracle VM Virtualbox Manager for 4.0.6) is very tiny and therefore unreadable, especially from the couch. I did not have this issue with VLC earlier this year when I was running the 32-bit version of Mythbuntu.

The XFCE Applications->Settings->Appearance->Fonts tab does not seem to affect these texts.

This is not an issue for me with VLC or Okular since this is a TV-computer primarily and most stuff is done using MythTV. However, I'm trying to set up Virtualbox so I can run Windows in it and use the Windows Skype client to videochat (currently we're booting into Windows to accomplish that), so I actually need to see what that program is trying to tell me.

This doesn't seem to affect any of the other programs I have installed: Firefox, Mousepad, Terminal, and Thunar file manager are the programs I use most often and these don't seem to be affected by this.

Does anyone have any thoughts on what is going on here?

Thanks in advance,
-Dan

---

### Post by DanBender on 2011-05-02
[Google search is friend, even when searching for stuff on this site.]("http://ubuntuforums.org/showthread.php?t=76141")
```
mousepad /home/*username*/.config/xfce4/Xft.xrdb

[add line]

Xft.dpi: 96
```

---

