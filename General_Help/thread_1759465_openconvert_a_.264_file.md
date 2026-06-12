---
title: "open/convert a .264 file?"
date: 2011-05-15
forum: General Help
---

### Post by chellrose on 2011-05-15
Someone has asked me to convert a video file for them.  The file came from their DVR, and it is named file.264.  I've tried various suggestions from a Google search, but with no success.  Does anyone know how to open such a file?  Thanks.

---

### Post by SeijiSensei on 2011-05-15
I'd try **mplayer**.  Given the name it's probably a file encoded with the H.264 codec which is pretty much the standard for HD.

Install mplayer from the repositories, then type "mplayer /path/to/file.264" at a command prompt and see what happens. mplayer will give you a lot of information on what it finds in that file and whether it can play it.

---

### Post by andrew.46 on 2011-05-16
As SeijiSensei has suggested MPlayer would be your best bet but you may find that MPlayer will barf on some raw h.264 streams. If so simply mux it into a container such as mp4 with MP4Box or matroska with mkvmerge and then it should play ok.

---

### Post by chellrose on 2011-05-16
Thanks for the responses.  I couldn't get MP4Box working in either Windows or Wine (Windows complained about a missing dll file; Wine insisted I install Mono, which I couldn't find in the repositories).

mplayer wouldn't play the file.  Here is the output:

```

myun@mycomp:~$ mplayer Desktop/file.264
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Desktop/file.264.
H264-ES file format detected.
FPS not specified in the header or invalid, use the -fps option.
No stream found.


Exiting... (End of file)

myun@mycomp:~$ mplayer -fps=25 Desktop/file.264
Unknown option on the command line: -fps=25
Error parsing option on the command line: -fps=25
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team

```
From the man page, fps=25 appeared to be the correct way to set that option...



So, I tried mkvmerge.  It gave me a strange error message:

>  Error: '/home/myun/Desktop/file.264' track 0: mkvmerge encountered broken or unparsable data in this AVC/h.264 video track. Either your file is damaged (which mkvmerge cannot cope with yet) or this is a bug in mkvmerge itself. The error message was:
There really was nothing in that area where there is supposed to be an error message.  Any other suggestions?

Thanks. :)

---

### Post by SeijiSensei on 2011-05-17
-fps doesn't take an equals sign.  Most of the major mplayer parameters don't either.

Usually frame rates are ~24 fps for progressive encodes and ~30 for NTSC video.  The actual values are fractionally smaller and should be entered as follows:

for 24 fps use "-fps 24000/1001"
for 30 fps use "-fps 30000/1001"

mplayer can interpret these fractions and will represent them internally as floating point numbers.

---

### Post by anjilslaire on 2011-05-17
Have you tried Handbrake?

---

### Post by chellrose on 2011-05-17
Thanks.  mplayer at least opens the file with those options, though the playback falters in several places.  I have no idea what the actual frame rate is; I tried both of your examples, and mplayer at least opened the video...

I've not tried Handbrake.  I'll look into it.

Update: I installed both the GUI and CLI versions of handbrake from the repositories listed on their website.  I can't get the cli version to run -- there doesn't appear to be an executable, just a bunch of documentation, none of which pertains to the actual operation of the program.  In the GUI, I selected my file as the source.  The program seems to scan it quickly and then reverts to Source:None.  I can't find anything resembling an error log.  Is there a step I'm missing?

---

### Post by pricetech on 2011-05-17
Not that I can help you read it, but I suspect the issue is a proprietary codec.  We have a DVR here that outputs some seriously oddball videos that can only be played with the vendor's player software.

Is that an option for you ??

---

### Post by chellrose on 2011-05-18
That may be it.  I'll try to find out what kind of DVR my friend has.  Thanks for the suggestion.

---

