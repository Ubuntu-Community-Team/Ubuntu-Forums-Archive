---
title: "Burn compatibility with Windows (&gt;64 char)"
date: 2010-01-06
forum: General Help
---

### Post by Dobbs5578 on 2010-01-06
[disclaimer: noob]
I have found the wonder that is FLAC and am encoding CD's. My system at work is locked down so I found CoolPlayer++ to play FLAC which I intended to play from a DVD I created. I have collected my FLAC into collections that I want to burn to DVD for playback. So, I burn DVD in Ubuntu (9.04), files look and work great from within Linux. When I use in Windows all the folders and files are 8.3 format (major issue is that .FLAC are now .FLA and not recognized by CoolPlayer). However, if I use Windows compatibility then the FLAC filenames are truncated to 64 char (many are longer since they have track number, and full song names). Is there a way to keep longer than 64 and use in Windows?

---

### Post by cariboo on 2010-01-06
It looks like there is a bug in Brasero, that causes your problem. #[lpbug]416731[/lpbug]. I would suggest trying k3b, it is in the repositories.

---

