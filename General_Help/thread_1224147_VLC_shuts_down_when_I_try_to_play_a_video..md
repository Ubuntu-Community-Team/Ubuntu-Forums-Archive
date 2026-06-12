---
title: "VLC shuts down when I try to play a video."
date: 2009-07-27
forum: General Help
---

### Post by qwerty57 on 2009-07-27
I've got a very strange  problem!  First, I'm using Jaunty unr on an Acer Aspire Laptop.  Earlier today I plugged a VGA cable in and tried to use the second monitor (actually a projector) function (system/preferences/display).  After struggling with the computer for about 10 minutes (much to the amusement of my students) I finally got the second screen working.  However, when I tried to play a video with VLC, the video would open and then immediately shut down!  I tried using the standard movie player and the same thing happened.  As soon as the movie started, the program would end.  

I've obviously messed things up and the videos are probably disappearing onto some non-existent monitor or something like that.  Does anyone have any ideas as to how to solve this?:confused:

TIA!

I forgot to mention that VLC and the regular video player both worked fine before I tried to set up the dual monitor thing.

---

### Post by SyL on 2009-07-27
Few things i would to in order to troubleshot the issue:
- is VLC crashing? --> run the command top or just look at the process list in the system management window. Also run VLC from a terminal in order to get the output logs...
- is the video corrupted? --> able to read the same video on your main computer screen as well?
- is VLC displayed on a ghost monitor? --> have a look here: [http://mailman.videolan.org/pipermail/vlc/2004-January/007182.html](http://mailman.videolan.org/pipermail/vlc/2004-January/007182.html)

HTH

---

### Post by qwerty57 on 2009-07-27
Thanks, that really helps pinpoint the problem!  The video is fine, I just played it (an MP4) on my desktop computer without any problems.  So, I turned on my Laptop and I started vlc with the system monitor on & saw that it was really shutting down, so it wasn't playing on a ghost monitor.  Finally I started it in terminal mode & got this error message:  **BadAlloc (insufficient resources for operation)**

I tried the standard Totem movie player and got exactly the same error message.

If I had this problem in Windows, I would just uninstall the programs and reinstall them.  Should I try that with Unbuntu? 

Oddly enough, I can play music, but not videos!  

Thanks again!

---

### Post by binbash on 2009-07-27
go to vlc preferences and change the video output to X11

---

### Post by Exore on 2009-08-09
> **binbash said:**
> go to vlc preferences and change the video output to X11

Thanks, that worked for me!

---

