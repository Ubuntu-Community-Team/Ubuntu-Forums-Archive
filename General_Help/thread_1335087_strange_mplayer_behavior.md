---
title: "strange mplayer behavior"
date: 2009-11-23
forum: General Help
---

### Post by viking_maniac on 2009-11-23
Today I was giving the default mplayer for Karmic a go to test some different video formats. At first, mplayer couldn't play anything. Then I realized that I had to choose audio and video outputs, along with a default codec for video and audio. So I started to play around with different outputs and codecs, but suddenly, with one type of video files, the mplayer got insane. It crashed and didn't want to play at all. I couldn't even close the app. Actually, I couldn't even kill the service with the sudo kill PID# command!! I had to reboot the whole OS! With further testing, I suddenly noticed, and I was not drunk, that mplayer suddenly was run and owned by root, even though I started mplayer with a second user account with no sudo privileges at all! I'm pretty sure that this is what I was seeing on the system monitor.
 
I'm just wondering if anyone else have been noticing this strange behavior, or have some kind of explanation to what just happened there. Thanks!

---

