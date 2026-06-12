---
title: "amaroK 1.4 and gstreamer"
date: 2006-06-11
forum: General Help
---

### Post by uthfull on 2006-06-11
Is there any way by which I could install the gstreamer engine fir amaroK 1.4 ? I have mp3s playing with xine but the quality of sound is not up to the mark and there is some sort of distortion.

Please help..... I'm  a total n0ob !!

---

### Post by manicka on 2006-06-11
Open the Volume control panel by right clicking on the volume icon and choosing 'Open Volume Control'.

Make sure that your PCM volume level is not set to high. This can cause distortion. About 70% works well for me.

HTH :)

---

### Post by manicka on 2006-06-11
P.S. Personally I'd stick with the xine engine. Gstreamer causes to many headaches, despite the improvements in it.

---

### Post by matrooswolf on 2006-06-11
I'm not sure but I don't think gstreamer is supported for amarok 1.4 (can anybody confirm this?) 

Xine works fine for me

---

### Post by ticool on 2006-06-11
No no, therae is an official list of supported soundmachines... 
gstreamer is one of them and i think it was the prefered one by the developers.

---

### Post by Jucato on 2006-06-11
I was under the impression that the GStreamer backend has been broken in KDE since last month. I guess no one is working on that right now. That's just AFAIK.

---

### Post by matrooswolf on 2006-06-11
[QUOTE=ticool]No no, therae is an official list of supported soundmachines... 
gstreamer is one of them and i think it was the prefered one by the developers.[/QUOTE]
Are you sure about that?  I thought they disabled gstreamer in amarok 1.4 (quote from wikipedia.)
>  GStreamer (disabled in 1.4 due to a lack of maintainer)
And I only find amarok-xine in synaptic ...

---

### Post by uthfull on 2006-06-11
Lowering the PCM level worked. The sound quality has definitely improved. But I never faced any such problem in SUSE. The PCM level was max and the sound output was awesome.

One more thing. I could start a new thread but wats the use. Ubuntu auto mounted all my partitions, 3 of them. All are FAT32. Now the partitions are somewhat writeable but not fully as some files and folders have a lock on them.

Further, the partition where Ubuntu is installed, FileSystem, how do I make it writeable. Whenever I wish to edit anything, I have to go to the terminal and type gedit blah blah blah. If I double click and open it, it opens as read-only. Help!!

---

