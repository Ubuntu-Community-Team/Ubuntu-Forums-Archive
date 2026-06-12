---
title: "Video thumbnail preview"
date: 2011-03-20
forum: General Help
---

### Post by gofurygo on 2011-03-20
Hi there...

I have kind of an odd "problem" with preview thumbnails of video files.

I store most of my videos on an external usb disk for travelling. After I first connected this disk to Ubuntu (10.10) it generated the movie thumbnails. I ripped a few more dvds with dvd:rip and copied those avi files to the usb drive. Oddly enough, I didnt get any preview thumnail on the new files. I deleted all files .thumbnails in my /home/ directory to force the regeneration of those thumbnails and it worked with all pictures I have...but not with the movie files. Now, I dont even get thumnails on the files that showed fine before... 

Thumbnail creation is set to "files smaller than 1GB" through nautilus/properties and to "local files only"...  all movie files are associated with VLC...

What am I missing? Thanks in advance guys...

---

### Post by Krytarik on 2011-03-20
Please see my earlier post regarding this, for you it's of course the other way around:
[http://ubuntuforums.org/showthread.php?p=10225467](http://ubuntuforums.org/showthread.php?p=10225467)

---

### Post by gofurygo on 2011-03-20
This option in gconf-editor was already enabled... Nevertheless, your hint helped me to find out where the problem is.
When I first installed ubuntu, Totem was still the standard videoplayer --> thats where all the thumbnails where created nicely on the usb drive at first. After that I removed totem and replaced it by VLC. So of course, after deleting the .thumbnails directory, everything was gone and was not recreated. The path to the thumbnail creator for all video files in the gconf-editor is > /usr/bin/totem-video-thumbnailer -s %s %u %oSo obviously, I have 2 questions now...

1) Why is this not automatically corrected when installing VLC?
2) What path do I need to use to relate the thumbnail creation with VLC?

Thanks ;-)

EDIT:
I did some further research. It seems Totem provides the thumbnailer for Nautilus. Since I removed Totem, the thumbnailer is also gone. VLC does not provide a thumbnailer. In Synaptics, I found ffmpeg-thumbnailer and installed it. I changed the path of the .avi file in gconf-editor, signed off and on again...but to no avail... :-(  How can I tell nautilus to use ffmpeg-thumbnailer as video thumbnailer?

---

### Post by Krytarik on 2011-03-20
How about this command instead?:
[http://code.google.com/p/ffmpegthumbnailer/wiki/Faq](http://code.google.com/p/ffmpegthumbnailer/wiki/Faq)

---

### Post by gofurygo on 2011-03-20
Thank you very much, that did the trick... ;-)

I do have another question though... How do I make thumbnails for rmvb (realvideo) files? I tried to change all realmedia related entries in gconf-editor to the ffmpegthumbnailer command, but videos still wont show thumbnails, even after deleting the files in .thumbnails...

I found this thread...
[http://ubuntuforums.org/showthread.php?t=278162](http://ubuntuforums.org/showthread.php?t=278162) it describes to do it for mplayer but not for ffmpeg
...isnt there an easier way to do this for rmvb...?

Cheers ;-)

---

### Post by Krytarik on 2011-03-21
You did already set the command for this mimetype?: "application@vnd.rn-realmedia"
And it didn't work?

Maybe because ffmpeg can't decode those files?

Which app is able to play those files at your system?

---

### Post by gofurygo on 2011-03-21
Yes, I set the command and its enabled. But its not working...

I think you are right... at least I couldnt find any hint online that ffmpeg is able to handle rmvb files, mencoder can though.

The rmvb files are played nicely with VLC...

So do I have to live without thumbnails for .rmvb after removing Totem..?

---

### Post by Krytarik on 2011-03-21
You could try to find a command to use either mencoder or VLC to create the thumbnails.

---

### Post by gofurygo on 2011-03-21
I did some research on vlc thumbnail commands... best thing i found was this..

[http://wiki.videolan.org/LibVLC_SampleCode_Thumbnailer](http://wiki.videolan.org/LibVLC_SampleCode_Thumbnailer)

but to be honest, I have no clue what to do with it :-)

---

### Post by Krytarik on 2011-03-22
I already did a websearch yesterday, and now again. But aside from the site you already found, I could only find this one, and it states the given commands as Window commands, I hope you can do something with it:
[http://wiki.videolan.org/How_to_create_thumbnails](http://wiki.videolan.org/How_to_create_thumbnails)

The code from the site you found is apparently C source code.

---

