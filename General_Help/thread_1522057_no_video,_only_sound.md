---
title: "no video, only sound"
date: 2010-07-01
forum: General Help
---

### Post by Smart Viking on 2010-07-01
Hey,

Im on a ubuntu computer now, and when i play video files, i only get sound, no video. Flash works fine, the video is there. It is like that with a big .avi file i tried, and also when i play DVD's from the cd drive.

Please ask for any further information. :)

EDIT: Before i installed a new graphics card and installed drivers, if i remember right, the video from a DVD would just make the video player disappear without any notificasion.
 I have tried both with the default ubuntu media player, and VLC.

---

### Post by Smart Viking on 2010-07-01
Wow i found the problem, and it was kinda weird since i'm pretty sure noone have changed any settings for totem...

First i tried to play the movie from the terminal with "mplayer" and for some reason it worked, but i could not reproduce that, it wouldn't play correctly when i tried after the first time, so i opened it in totem, went to "edit->properties->video" (sorry if that is slightly wrong, this machine uses norwegian) and i saw the "contrast" was set all the way down, so there simply was no contrast and everything was therefor black on the screen. I guess it doesn't have anything to do with totem, since i had the same problem with other media players, rather Ubuntu that was giving videos "0" contrast by default. When i changed the settings in one video, the other videos worked too. :)

---

### Post by viragoboy on 2011-03-14
Excellent! I've been pulling my hair out trying to figure out why I could get sound but no video. Contrast at zero.

Thanks.

---

