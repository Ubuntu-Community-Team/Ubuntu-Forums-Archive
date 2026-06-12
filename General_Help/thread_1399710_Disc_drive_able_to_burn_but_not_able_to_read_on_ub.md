---
title: "Disc drive able to burn but not able to read on ubuntu."
date: 2010-02-06
forum: General Help
---

### Post by SpenceMakesSense on 2010-02-06
My current dvd drive I had in is able to burn DVDs and CDs no problem. But when trying to play a DVD movie or an audio CD whatever I use to try to play them crashes or gives me an error message. But on windows it works fine. Heres some terminal outputs for when I run them in different media players.

Totem: ```
** (totem:4895): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
** Message: Error: Could not read from resource.
gstfilesrc.c(872): gst_file_src_create_read (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstFileSrc:source:
system error: Input/output error

```

VLC: ```
 

VLC media player 1.0.2 Goldeneye
[0x8f0d140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: HARVEY_BIRDMAN_VOL_1_DISC_1
libdvdnav: DVD Serial Number: 32426122
libdvdnav: DVD Title (Alternative): HARVEY_BIRDMAN_VOL_1_DISC_1
libdvdnav: Unable to find map file '/home/spence/.dvdnav/HARVEY_BIRDMAN_VOL_1_DISC_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f00000. Regions: 1 2 3 4
libdvdnav: Suspected RCE Region Protection!!!
[0xb7401eb8] main input error: ES_OUT_RESET_PCR called
[0xb7401eb8] main input error: ES_OUT_RESET_PCR called
[0xb7401eb8] main input error: ES_OUT_RESET_PCR called
[0xb7401eb8] main input error: ES_OUT_RESET_PCR called

```

xine doesnt give much of a terminal output but I'll include the error message it gives me with a pic. 
I'm using Ubuntu 9.10 
Hope I gave enough info and thanks in advance!

---

### Post by SpenceMakesSense on 2010-02-06
bump

---

### Post by stoneage on 2010-02-06
> **  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information. 
> Suspected RCE Region Protection!!!


Install libdvdcss2 and libdvdread

Also try here for more information:-
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
[https://help.ubuntu.com/7.04/musicvideophotos/C/video.html](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html)

Due to copyright issues Ubuntu can't be shipped with proprietary packages and remain free, so some things you need to do yourself.

---

### Post by SpenceMakesSense on 2010-02-06
That seemed that had gotten DVDs to play in totem and xine(no VLC though but thats not a problem) My next problem would be audio cds not working.  Heres what I get outputs for in Rhythmbox and VlC

rhythmbox:```
** (rhythmbox:7525): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:7525): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

** (rhythmbox:7525): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:7525): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:7525): GStreamer-WARNING **: Name queue is not unique in bin uridecodebin0, not adding

(rhythmbox:7525): GStreamer-CRITICAL **: gst_caps_get_structure: assertion `index < caps->structs->len' failed

(rhythmbox:7525): GStreamer-CRITICAL **: gst_structure_get_name: assertion `structure != NULL' failed

(rhythmbox:7525): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

(rhythmbox:7525): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

(rhythmbox:7525): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

(rhythmbox:7525): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

(rhythmbox:7525): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

(rhythmbox:7525): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

(rhythmbox:7525): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

``` Gives an error box that says data flow error

VLC:```
VLC media player 1.0.2 Goldeneye
[0x8cdb140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x900d108] main input error: open of `cdda:// &#65533;&#543;&#1553;&#65533;&#65533;' failed: (null)

``` There could be a problem with VLC in general though.

---

### Post by stoneage on 2010-02-06
Sorry, I don't know, possibly it is a codec problem?

What file format are the audio files?
Do you have sound in other applications like movies and web video?

You could try installing non-free-codecs or ubuntu-restricted-extras.

It might also be worth having a look around in the multimedia forums.

Hope you find the solution......

---

### Post by SpenceMakesSense on 2010-02-08
so it turns out it was doing this with my flash drive also. If I tried to copy files onto it it would say "input/output" error. Since I have my /home separate I went ahead and did a reinstall and it fixed all the problems I was having. Thanks for the info about playing DVD videos  though :popcorn:

---

