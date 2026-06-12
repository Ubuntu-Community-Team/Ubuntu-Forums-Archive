---
title: "Total system crash after attempt to play an MP3 on Lucid!"
date: 2010-05-15
forum: General Help
---

### Post by Macchi on 2010-05-15
Today while browsing the web and attempting to listen to a mp3 file on the site of a musician, this laptop with Lucid CRASHED badly! It went into a black screen and the only solution was a reboot! I am not a masochist, but I could repeat the crash a couple of times just to verify it.


This is the worst crash that I have seen on GNU/Linux! I expect things to go down in a more controlled way: maybe first the crash of a plug-in, then the crash of a web browser, eventually the crash of a windows manager. But I don't like seeing that playing an mp3 is leading to kernel crash on what is supposed to be a LTS-release! 

Any observations of similar behavior or hints on the cause?
Is it possible that the crash is related to intel graphics 85x on this system that are now very problematic on Lucid?








PS: I am not posting the link because I don't want to risk crashing lots of systems for other forum visitors! 
By the way, the music file in question is probably not malformed and plays perfectly on Mac and Windows. I am digging into system logs to try to find any record of the problem. For the the record: I am not a newbie since I've been around Ubuntu since 5.04, on Linux since 2003, on Unix since 1988, and on computers since 1979.

---

### Post by TeoBigusGeekus on 2010-05-15
Post us the link!

---

### Post by Macchi on 2010-05-15
Now I have more information and can confirm my suspicions of problems with the graphics manager. Mp3 playing is OK and the bug must be related to kernel modules etc for graphics and X. Everything crashes when Firefox attempts to play mp3 files with visualizations, the default setting!

I new already that Lucid Lynx is unreliable and has problematic software for intel integrated graphic managers. It is a very bad thing for a LTS-release, please help us to solve this.

I can download the sample mp3-file directly with wget and play it with Mplayer and Rhythmbox without any problems. But upon attempts to play via Firefox the whole system crashes!

WARNING THIS LINK MAY CRASH SYSTEMS with intel graphic managers: [http://www.magnuslindgren.com/audio/track6batu.mp3](http://www.magnuslindgren.com/audio/track6batu.mp3)

---

### Post by TeoBigusGeekus on 2010-05-15
Everything works perfectly with Opera, as well as Chrome. Try them please and post back.

---

### Post by Macchi on 2010-05-16
I will not try other browsers because changing the browser is not a solution. I believe that the problem must be related to graphics management at a kernel level. 

The serious bug that afflicts this system is certainly not repeatable for any generic Ubuntu system, but probably can be repeated with similar system configurations havin intel integrated graphics 85x etc. To get this system past a blank screen after boot of Lucic clean install I had to apply the first workaround at [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) . 






PS: I had high hopes on 10.04 LTS but now I feel like almost giving up this release as well. The former 9.10 was catastrophic for many of our systems at work and at home. The older 8.04 LTS was a candidate but has very limited functionality on many devices that we need. So the trade-off is hopeless: Older Ubuntu versions do not work with required devices and newer versions are unstable.

---

