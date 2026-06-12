---
title: "cannot play .pls in ubuntu 10.04"
date: 2010-10-11
forum: General Help
---

### Post by squishjt on 2010-10-11
Hi guys, for some reason i cannot play any .pls files anymore. i like to listen to a radio station on a website i visit. the addy is [http://184.82.19.16:8300/listen.pls](http://184.82.19.16:8300/listen.pls) it used to work fine till I upgraded and it still works on my laptop. Ive tried all the media players available. VLC has always been the one for me and not working anymore. any ideas?  thanks to all replies in advance.

---

### Post by andrew.46 on 2010-10-11
Hi squish,

Have you tested the stream with something simple like mpg123? Try:

```
sudo apt-get install mpg123
```

and then try the stream as follows on the silent computer:

```

andrew@ilium:~$ **[COLOR="Red"]mpg123 -C --long-tag -v -@ http://184.82.19.16:8300/listen.pls[/COLOR]**
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layers 1, 2 and 3
	version 1.12.1; written and copyright by Michael Hipp and others
	free software (LGPL/GPL) without any warranty but with best wishes
Decoder: SSE
Using playlist from http://184.82.19.16:8300/listen.pls ...
Note: Interpreting as PLS (Winamp/Shoutcast) playlist

Directory: http://184.82.19.16:8300/

Terminal control enabled, press 'h' for listing of keys and functions.

Playing MPEG stream 1 of 1:  ...
ICY-NAME: 
ICY-URL: 
MPEG 1.0, Layer: III, Freq: 44100, mode: Joint-Stereo, modext: 2, BPF : 313
Channels: 2, copyright: No, original: No, CRC: No, emphasis: 0.
Bitrate: 96 kbit/s Extension value: 0
Frame#    96 [    0], Time: 00:02.50 [00:00.00], RVA:   off, Vol: 100(100)
ICY-META: StreamTitle='Tir Na Saor';StreamUrl='';
Frame#   512 [    0], Time: 00:13.37 [00:00.00], RVA:   off, Vol: 100(100)
[0:13] Decoding of  finished.

```

Use the letter 'q' to halt the stream :).

Andrew

---

### Post by squishjt on 2010-10-12
thanks andy, tried that this is what happened.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  firefox-3.5-branding podsleuth odbcinst libboo2.0.9-cil unixodbc sdparm
  ethtool odbcinst1debian1 libwebkit1.1-cil
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  mpg123
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
2 not fully installed or removed.
Need to get 145kB of archives.
After this operation, 426kB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe mpg123 1.12.1-0ubuntu1 [145kB]
Fetched 145kB in 0s (395kB/s)
Selecting previously deselected package mpg123.
(Reading database ... 197912 files and directories currently installed.)
Unpacking mpg123 (from .../mpg123_1.12.1-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up firefox-4.0-core (4.0~b8~hg20101007r55015+nobinonly-0ubuntu1~umd1~lucid) ...
update-alternatives: error: alternative path /usr/bin/firefox-4.0 doesn't exist.
dpkg: error processing firefox-4.0-core (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-3.7:
 firefox-3.7 depends on firefox-4.0-core; however:
  Package firefox-4.0-core is not configured yet.
dpkg: error processing firefox-3.7 (--configure):
 dependency problems - leaving unconfigured
Setting up mpg123 (1.12.1-0ubuntu1) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            update-alternatives: using /usr/bin/mpg123.bin to provide /usr/bin/mpg123 (mpg123) in auto mode.
update-alternatives: using /usr/bin/mpg123.bin to provide /usr/bin/mp3-decoder (mp3-decoder) in auto mode.

Errors were encountered while processing:
 firefox-4.0-core
 firefox-3.7
E: Sub-process /usr/bin/dpkg returned an error code (1)
craig@Home:~$ mpg123 -C --long-tag -v -@ [http://184.82.19.16:8300/listen.pls](http://184.82.19.16:8300/listen.pls)
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layers 1, 2 and 3
    version 1.12.1; written and copyright by Michael Hipp and others
    free software (LGPL/GPL) without any warranty but with best wishes
Decoder: SSE
[resolver.c:218] error: connecton failed: Connection timed out
[resolver.c:306] error: Cannot resolve/connect to 184.82.19.16:8300!
[httpget.c:579] error: Unable to establish connection to 184.82.19.16
[playlist.c:271] error: Invalid playlist from http_open()!

---

