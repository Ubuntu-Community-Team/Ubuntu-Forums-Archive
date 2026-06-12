---
title: "wine pspvideo9 problem"
date: 2006-01-21
forum: General Help
---

### Post by emerick7 on 2006-01-21
I've been trying to get pspvideo9 working with wine so I can convert videos to the psp format (mp4). The wine installation seems to be working, but I can't run the pspvideo9.exe. I've been trying to run it through a terminal, but here's the output I get:

> ty@ubuntu:~$ wine z:\\home\\ty\\Desktop\\pspvideo9\\pspVideo9.exe
err:module:import_dll Library mscoree.dll (which is needed by L"Z:\\home\\ty\\Desktop\\pspvideo9\\pspVideo9.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\ty\\Desktop\\pspvideo9\\pspVideo9.exe" failed, status c0000135

Any idea what to do? Or is there any other known linux-compatible software for converting video formats (avi to mp4)? Thanks.

---

### Post by VR6Pete on 2006-01-21
What version of Wine are you using? 0.9.6 is the latest version available now.

---

### Post by emerick7 on 2006-01-21
I'm using 0.9.6 - just upgraded last night.

---

### Post by hellfire_bg on 2006-01-23
Why do you use pspvide9? If you know the correct file format, video resolution, bitrate and frames per second may be you could use another way to convert files.

---

### Post by siorai on 2006-01-23
I also tried to get pspvideo9 working in wine. It never worked. So I took a more complex route to using it: VMWare Player. I followed the guide here: [HowTo: Install XP in VMWare Player]("http://www.ubuntuforums.org/showthread.php?t=84275&highlight=vmware") and do all my psp converting in that. I also setup shares with samba so that once the videos are converted, I just move them over so they are accessible within Ubuntu.

---

