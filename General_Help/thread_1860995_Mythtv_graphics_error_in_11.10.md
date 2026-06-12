---
title: "Mythtv graphics error in 11.10"
date: 2011-10-15
forum: General Help
---

### Post by PhonicLynx on 2011-10-15
Just did a fresh install of Ubuntu 11.10 and installed the driver from AMD 11.9 and the driver from the additional drivers (with a totally fresh install) and my mythtv displays some really odd pink lines then showing the TV.

It doesn't happen on every channel but it seems its mostly the high definition streams.

Just to show you what I mean.. I uploaded a video to youtube here: [http://www.youtube.com/watch?v=5EiiPcBKfUo]("http://www.youtube.com/watch?v=5EiiPcBKfUo")

---

### Post by abusername on 2011-10-15
I am having the same issue, but this was an upgrade from 11.04.

---

### Post by sploutchy on 2011-10-15
Same thing for me upgrading from 11.04.

---

### Post by abusername on 2011-10-16
Recordings look fine when viewed outside of mythtv.  Playback or recorded or livetv shows vertical pink lines.

---

### Post by PhonicLynx on 2011-10-16
Mine are doing it in recordings AND live TV.

I think it depends on which channel your viewing.If you have a high def video it goes pink if you have a SD channel it displayes okay.

---

### Post by jem on 2011-10-17
Odd pink vertical lines in HD, either Live TV or recorded.  SD is fine.
Using proprietary Nvidia drivers, but I got similar behavior from the open-source drivers, but with some delay in SD processing.  HD recordings play OK, so it's looking like this is a MythTV problem.

---

### Post by syntr on 2011-10-17
I had this very same problem, and I thought my card was fried. Here's what fixed it for me (on an Intel i5-2500 using the integrated graphics):


[LIST=1]
[*]Open the MythTV frontend.
[*]Go to "Utilities/Setup"
[*]"Setup"
[*]"TV Settings"
[*]"Playback"
[*]Hit "Next" until you're on screen 3/8, "Playback Profiles"
[*]Change "Current Video Playback Profile" to Slim
[/LIST]

I'm not sure why this works, but it does ;)

---

### Post by PhonicLynx on 2011-10-17
I did the same thing in the end after what someone commented on the youtube post. Except I put it to highest resolution and it worked nicely. Having said that my cards are fairly high end so I didn't expect it to fail.

---

### Post by abusername on 2011-10-17
Thanks Syntr, that cleared up the problem!

---

### Post by josejuan05 on 2011-10-17
Someone in another post suggested this, and it turns out to be correct: The bug is in libmpeg2, so you can work around it by using any playback profile that doesn't use that library.

---

### Post by gkinney3203 on 2011-10-20
Thanks! That fixed me up too!

---

### Post by sn9ke.eyes on 2012-03-16
Thanks, was real frustrated with this until I saw this post which worked for me too.

---

### Post by djsutton on 2012-03-31
Thanks, the fix worked for me too.  

Anybody know of a bug report for this libmpeg2 issue to track yet?

---

