---
title: "HDMI Audio output problem - ATI Graphics Card"
date: 2010-05-02
forum: General Help
---

### Post by CyberPrime on 2010-05-02
So, I just built a new HTPC and decided to give Ubuntu a whirl again. I downloaded and installed 10.04, and set about configuring it. Everything looked great, except my audio over HDMI didn't work. I enabled the proprietary ATI drivers, and bam! the audio works! Great. Only one problem: there's a two inch border around my TV (not there with the open source drivers), and Boxee flashes colors rather than playing videos (a known bug. It's fixed by not using the ATI proprietary drivers). So, I disabled the drivers, rebooted, and the Boxee video works, the border/gap is gone, but once again the audio doesn't work. I've been through all the sound settings, and I have everything set to the HDMI output, but still nothing. I've tried various fixes I've found through googling ([http://www.mythtv.org/wiki/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly](http://www.mythtv.org/wiki/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly) [http://ubuntuforums.org/showthread.php?t=1466111&highlight=ati+hdmi+audio&page=2](http://ubuntuforums.org/showthread.php?t=1466111&highlight=ati+hdmi+audio&page=2)), to no avail. Does anybody else have a similar (or the same) problem? How did you fix it? Thanks.

---

### Post by CyberPrime on 2010-05-02
Sorry to bump so soon, but I know this will quickly get buried beneath all the other bug reports if I don't. Any help?

---

### Post by CyberPrime on 2010-05-03
Nobody? I know there's a solution out there somewhere.

---

### Post by Sandertje on 2010-05-03
I had exactly the same problem, and you have to edit asla-base.conf to fix it:

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

Than add this line to the file. this worked for me, but i'm on a dell laptop. Dont know if this is gonna help for you. Make a backup just be on the safe side.

```
options snd-hda-intel model=dell-m6
```. 

Save it, and reboot.

Make sure to make a backup of the file, of course.

---

### Post by CyberPrime on 2010-05-03
So, I followed this tutorial on how to get my model: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and the first readout came out as "ALC662". I looked it up on the chart ([http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD](http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD)) and found it's corresponding "models", but none of them seem to conform to my motherboard or graphics card. I have an ASrock, which was built on an Intel G41. Auto and ASUS don't work. I suppose I can go through the list one by one.

---

