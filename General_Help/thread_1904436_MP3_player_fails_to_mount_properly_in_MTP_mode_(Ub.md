---
title: "MP3 player fails to mount properly in MTP mode (Ubuntu 11.10)"
date: 2012-01-04
forum: General Help
---

### Post by koleary on 2012-01-04
I have a Sandisk Sansa Clip MP3 player that is not mounting correctly since I did a clean install of Ubuntu 11.10.

I have installed the mtpfs and mtp-tools packages.  I also verified that I have the latest version of firmware for the MP3 player installed.

When I plug the MP3 player into my PC, it does not appear in either the Nautilus file manager nor under /media in terminal.

When I run the "mtp-detect" command I get the following:

```

[170] ~: mtp-detect
 *libmtp version: 1.1.0*
 *Listing raw device(s)*
 *Device 0 (VID=0781 and PID=7432) is a SanDisk Sansa Clip.*
 *   Found 1 device(s):*
 *   SanDisk: Sansa Clip (0781:7432) @ bus 1, dev 11*
 *Attempting to connect device(s)*
 
```After outputting "Attempting to connect device(s)" the system hangs and I have to do a control-C to get my cursor back.

Please note that if I put the MP3 player into MSC mode then it will mount correctly.  However the audio files that are on it do not appear:

```

[194] /media/SANSA CLIP: ll
 total 716
 drwx------ 2 kevin kevin   4096 1980-01-01 00:00 AUDIBLE
 drwx------ 2 kevin kevin   4096 1980-01-01 00:00 AUDIOBOOKS
 -rw-r--r-- 1 kevin kevin    114 1980-01-01 00:00 DID.bin
 -rw-r--r-- 1 kevin kevin 688436 1980-01-01 00:00 MTABLE.SYS
 drwx------ 2 kevin kevin   4096 1980-01-01 00:00 MUSIC
 drwx------ 2 kevin kevin   4096 1980-01-01 00:00 PODCASTS
 drwx------ 4 kevin kevin   4096 1980-01-01 00:00 RECORD
 -rw-r--r-- 1 kevin kevin   5017 1980-01-01 00:00 RES_INFO.SYS
 -rw-r--r-- 1 kevin kevin    300 1980-01-01 00:00 SYS_CONF.SYS
 -rw-r--r-- 1 kevin kevin     83 1980-01-01 00:00 version.sdk
 [195] /media/SANSA CLIP: ls -a ./MUSIC
 .  ..
 [196] /media/SANSA CLIP: ls -a ./PODCASTS
 .  ..

```The reason that I want to use MTP mode is that I use gPodder for downloading podcasts and then I copy the podcast to my MP3 player.  MTP is the only mode that gPodder supports.

Please note that I was able to use this MP3 player in MTP mode with gPodder successfully under Ubuntu 11.04.

Any assistance you can offer would be appreciated.

Kevin

---

