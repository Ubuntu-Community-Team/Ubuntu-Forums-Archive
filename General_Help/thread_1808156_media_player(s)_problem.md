---
title: "media player(s) problem"
date: 2011-07-19
forum: General Help
---

### Post by nmxdaven on 2011-07-19
Hey guys,  I have a recurring problem with 11.04. For some reason, my media players stop working. (VLC and the default movie player)  After some amount of time (its been 1 hour to 2 days) my media players will stop working. Ill be watching a file, then the video will fail to load, followed by movie player crashing. Any attempts to open another file will show the movie player briefly, then the program will exit. (Less than a second) If I attempt to open the file in VLC after this has happens, it will play the sound, but not the video. I'm not doing anything in particular when this happens. It just seems random. A reboot will fix it until the next time. Anyone have any idea whats going on? I'm using the ATI catalyst drivers if that helps.   Thanks! nmxdaven

---

### Post by LowSky on 2011-07-20
Run vlc or totem (AKA: movie player) from a terminal, post the output, it may say what is failing.

What type of file exactly are they Divx, xvid, H.264, youtube videos? What size are they, are they over 4GB? How much hard drive space do you have? Did you install using Wubi? To better help you please give every detail about the computer you can. Just saying you are using ATI's drivers means little. Have you tried just loging out then back in, instead of rebooting?

---

### Post by nmxdaven on 2011-07-20
> **LowSky said:**
> Run vlc or totem (AKA: movie player) from a terminal, post the output, it may say what is failing.

What type of file exactly are they Divx, xvid, H.264, youtube videos? What size are they, are they over 4GB? How much hard drive space do you have? Did you install using Wubi? To better help you please give every detail about the computer you can. Just saying you are using ATI's drivers means little. Have you tried just loging out then back in, instead of rebooting?

 Thanks for the reply.  Ran totem from terminal and opened a file. It shot out,  > The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 105 error_code 2 request_code 133 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


VLC gets me,
> [0x9a6800] signals interface error: signal 17 overriden (0x7f0b5dbcc450)
[0x9a6800] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[0x9a6800] signals interface error: signal 17 overriden (0x7f0b5dbcc450)
[0x9a6800] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]


Files are around 200mb, various encodings (all play just fine after a reboot) Huge amount of free HHD. 
The version of totem im using was the one that was with the install. Vlc was installed using software center. Havnt tried to log out yet. I can't for a few hours, but ill try it later and see what happens.

---

### Post by LowSky on 2011-07-20
Hard drive size can be an issue if you gave / (root) its own partition and the /tmp or /var/log folders are filling up with garbage files.

---

### Post by nmxdaven on 2011-07-20
> **LowSky said:**
> Hard drive size can be an issue if you gave / (root) its own partition and the /tmp or /var/log folders are filling up with garbage files.

/ is set at 70gb, and conky is currently showing 5gb used.

---

### Post by SeijiSensei on 2011-07-20
Try installing **smplayer** from the repositories and see if it fares better.  It will install mplayer as the engine.

---

### Post by nmxdaven on 2011-07-20
> **SeijiSensei said:**
> Try installing **smplayer** from the repositories and see if it fares better.  It will install mplayer as the engine.

Just tried it and same issue. Audio but no video. I haven't been able to do a reset yet. I have a program for my thesis that has to run in 24 hour batches. Starting to get a bit frustrated without my southpark!

---

### Post by nmxdaven on 2011-07-20
[COLOR=Black]Was finally able to reboot. Tried just using [/COLOR][COLOR=Black]smplayer player this time. Same thing. Worked for about 2 hours, then no video. [/COLOR]

---

### Post by SeijiSensei on 2011-07-21
This sounds like a hardware problem.  Maybe the video card is overheating during extended playback and shuts down?  Have you checked the airflow in the machine? Maybe you need to clean out some gunk.  

Does the video card have an onboard fan?  Is it running most of the time?

---

### Post by nmxdaven on 2011-07-22
> **SeijiSensei said:**
> This sounds like a hardware problem.  Maybe the video card is overheating during extended playback and shuts down?  Have you checked the airflow in the machine? Maybe you need to clean out some gunk.  

Does the video card have an onboard fan?  Is it running most of the time?

No sir. I run several different os's, some of which get heavy gaming. Never a problem. 

I noticed some type of media player update come across the update manager today hoping that might solve something, but no avail. Getting a bit frustrated. I've searched around and no-one else seems to have had this problem. Not sure where to go from here.

---

