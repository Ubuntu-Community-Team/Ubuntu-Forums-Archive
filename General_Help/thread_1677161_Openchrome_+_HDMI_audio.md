---
title: "Openchrome + HDMI audio"
date: 2011-01-28
forum: General Help
---

### Post by wylie98 on 2011-01-28
Hi,
I wonder if anyone can help me here? I have a Jetway J7f5m MB with HDMI out. The board has a CX700m graphics chip and a VT1708 audio chip. I had video and audio working fine with Ubuntu 8.10 and VIA's open source drivers. Recently I updated the machine to ubuntu 10.10, using openchrome rather than via drivers as the CX700m graphics chip doesn't have a via driver newer than 9.04. I can get the video to work using this guide [http://ubuntuguide.net/ubuntu-10-10-fix-the-screen-messed-up-at-start-up-and-shutdown]("http://ubuntuguide.net/ubuntu-10-10-fix-the-screen-messed-up-at-start-up-and-shutdown")
 
 Unfortunately I can't get audio through the HDMI for the life of me. The Audio card seems to work analogue and unmuting the digital channels in alsamixer doesn't help. I have followed numerous guides and as far as i can tell the machine seems to play files fine and lists no errors when i force it to play through the digital device using 'aplay -vv -D plughw:0,1 track.wav'. Unfortunatly the audio doesn't seem to get to the HDMI interface. 
 
Could this be because openchrome needs to support this in some fashion or is it because the latest snd-hda-intel drivers have an error in them? And most importantly any idea how i fix it?


Thanks
Chris

---

