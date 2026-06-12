---
title: "problem with sound in Wine for just one program?"
date: 2010-01-02
forum: General Help
---

### Post by ILuvMontyPython on 2010-01-02
I have Wine installed in ubuntu/Kubuntu Jaunty and I can play games like Roller Coaster Tycoon fine in it (it works great and has sound)

but when I try to use my disk for Ear training (which is an .exe file) I can view/use the program perfectly except there is no sound, the disk works in the school computers so I know its not faulty, but the sound just doesn't work in Wine.

 I changed the format in Wine to all the different Windows (Vista, XP, 2000, etc.) and the sound didn't work in them either, 

everything in Alsa mixer is turned up 100% and I've tested it with both my head phones and computer speakers, but theres never any sound. 

I am just stumped on what to try next. any ideas?

---

### Post by ron999 on 2010-01-02
Hi
When I had sound problems with Spotify I found that by changing the wine Audio driver from ALSA to OSS cured it. I also had to install oss-compat from the repo.
So, try changing your wine Audio driver to OSS or EsounD.
Also you might get more support on the wine section of the forum.
Here:-[http://ubuntuforums.org/forumdisplay.php?f=313]("http://ubuntuforums.org/forumdisplay.php?f=313")
Good luck.
:)

---

