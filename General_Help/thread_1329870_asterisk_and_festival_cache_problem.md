---
title: "asterisk and festival cache problem"
date: 2009-11-17
forum: General Help
---

### Post by mvsjes2 on 2009-11-17
I've got a hardy system and am trying to get asterisk to work with festival. 

;
; Festival Configuration
;
[general]
;
; Host which runs the festival server (default : localhost);
;
;host=localhost
;
; Port on host where the festival server runs (default : 1314)
;
;port=1314
;
; Use cache (yes, no - defaults to no)
;
usecache=no
;
; If usecache=yes, a directory to store waveform cache files.
; The cache is never cleared (yet), so you must take care of cleaning it
; yourself (just delete any or all files from the cache).
; THIS DIRECTORY *MUST* EXIST and must be writable from the asterisk process.
; Defaults to /tmp/
;
;cachedir=/var/lib/asterisk/festivalcache/
;cachedir=/tmp/
;
; Festival command to send to the server.
; Defaults to: (tts_textasterisk "%s" 'file)(quit)\n
; %s is replaced by the desired text to say. The command MUST end with a
; (quit) directive, or the cache handling mechanism will hang. Do not
; forget the \n at the end.
;
;festivalcommand=(tts_textasterisk "%s" 'file)(quit)\n
;
;


No matter what I put in the festival.conf, I always get in the asterisk log:
[Nov 17 21:55:38] WARNING[24761]: app_festival.c:496 festival_exec: Unable to read from cache/festival fd

There are very few hits out there on this error. Has anyone else run into this?

---

### Post by mvsjes2 on 2009-11-18
Never mind about this. festival server seemed to have locked up my box. No more server for me. Will try scripting it.

---

