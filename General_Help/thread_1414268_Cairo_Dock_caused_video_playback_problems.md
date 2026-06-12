---
title: "Cairo Dock caused video playback problems"
date: 2010-02-23
forum: General Help
---

### Post by sbelz79 on 2010-02-23
I installed Cairo Dock last night, but unfortunately had to uninstall it because it was causing problems with video playback.  With VLC, the player would open, but just show through to the desktop where the video should be playing.  That was when the dock was running.  When I closed Cairo, any time I'd try to open a video in VLC, VLC would close entirely.

When I tried to open a video file in Banshee or Movie Player, the colors were all reversed- or at least it looked that way- people had blue skin (except in avatar where their skin was yellow-orange).

I uninstalled Cairo-dock and the problems went away.

I'm using Ubuntu 9.10 x86_64 on a machine with an AMD PhenomII x4 955, and I have a GeForce 9600 GSO video card.  I was running Cairo-Dock with Open GL.

I'd like to know if anyone knows how to fix this problem so I can use Cairo.

---

### Post by sbelz79 on 2010-02-23
OK, I solved this problem myself- I found the answer on the Cairo-Dock website (I always post my questions on the Ubuntu forum before I start looking for answers elsewhere- that way if I can't find the answer on my own, hopefully someone else has one by the time I'm done looking).

I disabled 'Embed video in interface' in VLC: Tools>preferences>interface settings.  I reinstalled Cairo-dock, and VLC is still working just fine.

---

### Post by dmakreshanski on 2010-03-04
opengl cairo-dock actually makes problems with a lot of video playing software (vlc, smplayer, skype, ...) that rely on xvideo extension.
apparently this is still an issue

[http://ubuntuforums.org/showthread.php?t=1231186](http://ubuntuforums.org/showthread.php?t=1231186)

---

### Post by cboteros on 2010-05-28
I also believe this isn't really solved.

For instance, adding the suggested code before does help in fixing the video, but brings other issues.

For example, using this command fixes Skype video:

```
export XLIB_SKIP_ARGB_VISUALS=1 && skype
```

But... now the taskbar icon of Skype doesn't have a transparent background as you can see here:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=158599&stc=1&d=1275090824[/IMG]

It is a minor problem, but anyway this should still be a motivation for developers of Cairo-dock to work on this.

---

### Post by cboteros on 2010-05-28
Btw,

I found out something interesting... 

[LIST=1]
[*]I deleted Cairo-Dock from my startup applications so when I logged in Ubuntu I didn't have Cairo-dock (System->Preferences->Statup applications)

[*]Then I started Skype without any special command, tested the video and it was fine.

[*]Then... I started Cairo-dock with open-GL, and the great surprise was that Skype video still worked fine, and the taskbar icon of Skype was looking fine also.
[/LIST]

So, it seems that the order in which applications are launched affects in this video problem (at least with Skype). 

This could be another "workaround", it is still not a solution though but maybe this information could give some light to Cairo-dock developers.

---

### Post by sbelz79 on 2010-05-28
Well, in any case, I'm satisfied.  Cairo Dock works reasonably well and I can watch videos.

---

### Post by fabounet on 2010-05-31
it's not Cairo-Dock that has a bug, but Qt
All Qt applications will have this bug whenever another application using transparent opengl is running (Skype, SMplayer, etc)

VLC also had it, but they could fix it in their own code.
I guess all programs using Qt could do the fix, but it would be simpler to just fix Qt, if only the devs would consider correcting the bugs...

---

