---
title: "Fresh 11.04 - no sound nVidia MCP51"
date: 2011-05-06
forum: General Help
---

### Post by Duvrazh on 2011-05-06
Hello, coming back to Ubuntu after not liking v8, installed 10.10 and upgraded to 11.04 during install process. I have a nvidia GTX 250 running video to a monitor and a tv and wanted to use my green center channel analog out on the back to send audio to the tv. (no room for hdmi, had to use VGA). 

I can't enable sound, I've Googled the crap out of this and have found my sound to be nVidia MCP51.

I'm not very Linux savvy, so if you need me to run commands please let me know what they are. Thank you for your assistance.:popcorn:

---

### Post by ivanovnegro on 2011-05-06
Hello.

Ok, maybe we can try first something easy, can you enable the proprietary drivers from System-> Additional drivers, to see if we can catch the drivers for your Nvidia sound card.

---

### Post by Duvrazh on 2011-05-06
> **ivanovnegro said:**
> Hello.

Ok, maybe we can try first something easy, can you enable the proprietary drivers from System-> Additional drivers, to see if we can catch the drivers for your Nvidia sound card.

Already using all the additional drivers just to get video out of the card. The sound mind you is coming from the motherboard. For more info about the box, the machine uses the original mobo from an [HP A1700N]("http://h10025.www1.hp.com/ewfrf/wc/documentSubCategory?tmp_rule=10449&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&site=null&lang=en&key=null&product=3339286").

---

### Post by ivanovnegro on 2011-05-06
Ok, now try to test your sound configuration. Is anything muted, is everything you need enabled?
You can look this when you click on the sound applet, then preferences.

---

### Post by Duvrazh on 2011-05-06
> **ivanovnegro said:**
> Ok, now try to test your sound configuration. Is anything muted, is everything you need enabled?
You can look this when you click on the sound applet, then preferences.

Everything looks good. I only see one audio device on the Hardware tab, it says Internal Audio, 1 output.

Should I not have more? My mobo has the headphone out on the front, the audio outs on the back plus a digital coax out. In addition, there is the graphics card which has HDMI, shouldn't that also show as an audio out?

---

### Post by ivanovnegro on 2011-05-06
Hm, not sure but that could be the problem.
Ok now we take a look in the terminal output of your mixers.

Type in a terminal:

```
alsamixer
```

and post the output back here.

---

### Post by Duvrazh on 2011-05-06
> **ivanovnegro said:**
> Hm, not sure but that could be the problem.
Ok now we take a look in the terminal output of your mixers.

Type in a terminal:

```
alsamixer
```

and post the output back here.

[Screenshot]("http://ubuntu.duvrazh.com/Screenshot.png")

I suppose it looks good to me. Perhaps another set of eyes would be more helpful.

---

### Post by ivanovnegro on 2011-05-06
Yep, looks normal for me too.
I think we need now some more assistance.

---

### Post by ivanovnegro on 2011-05-06
[Here]("http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+nVidia+MCP51") is some stuff in a thread, maybe you can find something regarding to your problem and [here]("https://help.ubuntu.com/community/SoundTroubleshooting") some documentation.

---

### Post by mdhollis on 2011-05-06
I have issues with my sound card as well.  My sound card is MCP61. I have tried numerous things with no success.  Basically I do not have digital audio but I do have analog.  I filed a bug about it. You have a different driver but maybe its related. 

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/773572]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/773572")

---

### Post by Duvrazh on 2011-05-06
> **ivanovnegro said:**
> [Here]("http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+nVidia+MCP51") is some stuff in a thread, maybe you can find something regarding to your problem and [here]("https://help.ubuntu.com/community/SoundTroubleshooting") some documentation.

Trying that thread now. The alsa site doesn't work the same as that instruction depicts it should. Reorg since writing? 

Also trying adding some packages through synaptic related to alsa to see if I can't stumble across a solution at the same time. I'll post findings when I've completed these tasks.

---

### Post by Duvrazh on 2011-05-06
> **Duvrazh said:**
> Trying that thread now. The alsa site doesn't work the same as that instruction depicts it should. Reorg since writing? 

Also trying adding some packages through synaptic related to alsa to see if I can't stumble across a solution at the same time. I'll post findings when I've completed these tasks.

I'm confused. In ALSAMIXER I get ALC888 as my sound card, but when I do lspci -v I see MCP51. Any ideas as to what I'm doing wrong? I went through the whole "comprehensive guide" and even recompiled the ALSA drivers, tried weening it down to HDA-xxxxxxx and still no sound at all.

This is not convincing me to switch my media server to ubuntu as it drives the living room tv when I can't even get the bedroom computer (which drives the bedroom tv) to make a single noise.

---

### Post by Duvrazh on 2011-05-06
Is anyone else running Natty on an HP Pavilion a1700n?

---

