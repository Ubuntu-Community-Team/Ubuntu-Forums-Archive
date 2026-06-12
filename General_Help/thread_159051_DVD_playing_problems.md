---
title: "DVD playing problems"
date: 2006-04-12
forum: General Help
---

### Post by Carandol on 2006-04-12
I'm having problems playing DVDs in Ubuntu 5.10. 

First of all, my difficulties with Totem...

With totem-gstreamer installed, I *can* play a DVD, but only in a very tiny window, which doesn't get any bigger when I try to go to full screen. 

When the program is run I get the following messages in the console:
----------------------

(totem:9553): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:9553): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

-------------------------

When DVD is started, I get the following messages:
---------------------------

libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: STAR_TREK_NEMESIS
libdvdnav: DVD Serial Number: 3EB0EE81___MVB__
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/carandol/.dvdnav/STAR_TREK_NEMESIS.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001b6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0003515b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00035190
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000351dd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00074189
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000741d6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000c468f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000c65eb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00331ba7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00331bf4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003537d4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00353821
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0037b45c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0037b4a9
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0
No accelerated IMDCT transform found
No accelerated IMDCT transform found
No accelerated IMDCT transform found
No accelerated IMDCT transform found
No accelerated IMDCT transform found
No accelerated IMDCT transform found
No accelerated IMDCT transform found
No accelerated IMDCT transform found

** (totem:9553): WARNING **: Not init!

---------------------------

If, instead, I use totem-xine as the engine, Totem loads, with the messages:

----------------------------

(totem:9763): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:9763): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

------------------------------


...but when I try to run a DVD, it immediately quits with the messages:

------------------------------

libdvdnav: Using dvdnav version 1.0.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: STAR_TREK_NEMESIS
libdvdnav: DVD Serial Number: 3EB0EE81___MVB__
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/carandol/.dvdnav/STAR_TREK_NEMESIS.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001b6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0003515b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00035190
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000351dd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00074189
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000741d6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000c468f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000c65eb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00331ba7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00331bf4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003537d4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00353821
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0037b45c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0037b4a9
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 158 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

--------------------------------

I've tried using VLC instead (even completely uninstalling Totem and all xine and gstreamer drivers). It doesn't give any error messages, but tends to lock up completely two or three times during a movie, requiring a hard reboot of the computer. It's also rather less smooth than it should be, despite having set the DMA correctly.

This *must* be a software problem, because I was playing DVDs with no problem at all in Kaffeine in OpenSUSE 10. I've tried using Kaffeine in Ubuntu, which much the same results as with Totem. 

(I've also tried MPlayer, which plays the soundtrack, but only has a blue screen).

Any help appreciated, as I much prefer Ubuntu to SUSE (it's much more fast and responsive on my old twin 600mhz machine than SUSE), but if I can't play DVDs sucessfully, it's not worth using.

---

### Post by mvaniersel on 2006-04-12
I can't help you with the totem problem, but besides DMA there is another reason why DVD playback might be bad: not getting hardware acceleration. Which video card and driver are you using?

---

### Post by Carandol on 2006-04-12
[QUOTE=mvaniersel]I can't help you with the totem problem, but besides DMA there is another reason why DVD playback might be bad: not getting hardware acceleration. Which video card and driver are you using?[/QUOTE]

Looking at Device Manager, it's a Matrox Millenium G400 16Mb SGRAM (MGA G400 AGP). I'm not sure where I'd look to find out what driver it's using. (I could find it in SUSE, but I'm new to Ubuntu...)

---

### Post by Perfect Storm on 2006-04-12
HOWTO matrox: [http://ubuntuforums.org/showthread.php?t=78288&highlight=matrox+xorg](http://ubuntuforums.org/showthread.php?t=78288&highlight=matrox+xorg)

---

### Post by Carandol on 2006-04-12
Thanks, I'll follow that up. I'll follow up your games list too!

---

### Post by Perfect Storm on 2006-04-12
The gamelist will be updated tomorrow, so check back the list tomorrow at same time  ;)

---

### Post by Carandol on 2006-04-12
Finally got the DVD working properly! I did it by installing Kaffeine, and setting the Player Engine to Kaffeine in the Settings menu. I then selected xine Engine Parameters in the Settings menu, then set the Audio Driver to esd and the Video Driver to xshm. It now works perfectly. I suggest this might be worth trying for others stuggling with DVD playback, since there are more options available than in the Gnome Systems/Preferences/Multimedia Systems Selector option.

---

### Post by Perfect Storm on 2006-04-12
You should also try give VLC a chance, it's very good IMHO.

---

### Post by ububaba on 2006-04-12
[QUOTE=Artificial Intelligence]You should also try give VLC a chance, it's very good IMHO.[/QUOTE]
 I have been using VLC and am fond of it. Earlier I could even play movies which are on
the XP HDs without any hitch, while I was logged in Ubuntu. Now it is impossible.
Neither can I copy nor move any stuff from XP HDs to Ubuntu HDs. After opening any 
file from XP HD, I am blocked out from Ubuntu. I loose my right to click on anything in 
Ubuntu.  A reboot is needed then. :shock:

What a spot to be in? Surely someone else has had to face this one. Please help me
get out of it. Thanks

---

### Post by Perfect Storm on 2006-04-12
I don't dual boot (running linux clean ;) ) but I have seen some threads around about the issue.

---

### Post by ububaba on 2006-04-12
[QUOTE=Artificial Intelligence]I don't dual boot (running linux clean ;) ) but I have seen some threads around about the issue.[/QUOTE]
I also thought so but unfortunately can't locate them. ](*,)

---

### Post by Perfect Storm on 2006-04-12
Then just start a new thread and explain your problem with so many information you have about the issue. Also tell step by step you do before it blocks you.

---

### Post by Carandol on 2006-04-12
[QUOTE=Artificial Intelligence]HOWTO matrox: [http://ubuntuforums.org/showthread.php?t=78288&highlight=matrox+xorg](http://ubuntuforums.org/showthread.php?t=78288&highlight=matrox+xorg)[/QUOTE]

Well, I gave that a try, but all it did was disable my graphics, which gave me an anxious few minutes while I got it working again...

Still, it was a learning experience :-)

---

