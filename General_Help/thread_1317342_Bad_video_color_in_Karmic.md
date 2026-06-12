---
title: "Bad video color in Karmic"
date: 2009-11-06
forum: General Help
---

### Post by codedmin on 2009-11-06
> **scathmandra said:**
> I've upgraded to Karmic and suddenly I can't play .avi files anymore, or stream .asx files from websites. VLC suggests that it's something I can't fix, but I beg to differ. Are there any other people with this problem? Any solutions out there?

Hy there, i can play videos, but they are colorless, the colors are all wrong :S attached file

I do upgrade from 9.04 to 9.10 too

---

### Post by DeMus on 2009-11-06
> **codedmin said:**
> Hy there, i can play videos, but they are colorless, the colors are all wrong :S attached file

I do upgrade from 9.04 to 9.10 too

Use this:

```
xvattr -a XV_HUE -v 0
```

There is an error which causes the HUE variable to be something else than 0. With this remedy you force it to be 0 again.
Whenever you play a video start this code. I know it's not ideal but it works.

---

### Post by codedmin on 2009-11-06
> **DeMus said:**
> Use this:

```
xvattr -a XV_HUE -v 0
```

There is an error which causes the HUE variable to be something else than 0. With this remedy you force it to be 0 again.
Whenever you play a video start this code. I know it's not ideal but it works.

Ok that almost work... after done that i have video ok in vlc, after that i try open totem to play the video and totem freeze, try again open video in vlc and is bad again, run again your command and works ok in vlc, so the problem is in gnome-player/totem?

---

### Post by DeMus on 2009-11-06
> **codedmin said:**
> Ok that almost work... after done that i have video ok in vlc, after that i try open totem to play the video and totem freeze, try again open video in vlc and is bad again, run again your command and works ok in vlc, so the problem is in gnome-player/totem?

Please read this thread:
[_Negative colors_]("http://ubuntuforums.org/showthread.php?t=791235"), maybe it helps.

---

### Post by codedmin on 2009-11-06
> **DeMus said:**
> Please read this thread:
[_Negative colors_]("http://ubuntuforums.org/showthread.php?t=791235"), maybe it helps.

That works, but i only can see videos in gnome-player if i open gnome-player and the drag the video, if i double click on video, the gnome-player freeze..

---

### Post by DeMus on 2009-11-06
> **codedmin said:**
> That works, but i only can see videos in gnome-player if i open gnome-player and the drag the video, if i double click on video, the gnome-player freeze..

That must be another error you have, this has nothing to do with the negative colors you are/were seeing.
Maybe you try another video, or re-install the player. Maybe that helps.

---

### Post by codedmin on 2009-11-06
> **DeMus said:**
> That must be another error you have, this has nothing to do with the negative colors you are/were seeing.
Maybe you try another video, or re-install the player. Maybe that helps.

Done that but no juice.. .like i said everytime totem freeze then negative colors are back again

---

### Post by Rocket2DMn on 2009-11-06
I have split your posts into a new thread - in the future, please don't hijack another user's thread for support.
BTW, I hear this is a bug in the nvidia proprietary driver.
Good luck.

---

