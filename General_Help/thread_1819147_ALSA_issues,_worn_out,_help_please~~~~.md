---
title: "ALSA issues, worn out, help please~~~~"
date: 2011-08-05
forum: General Help
---

### Post by sliter on 2011-08-05
Well, there is a long story about my experience in alsa.:(

In bref, i am still a noob to linux. When I started with Ubuntu 11.04, i found that there is no sound through my laptop speaker but ok with a headphone. So I followed different kinds of helps through internet. 

Now, the problem seems that i've destroyed my alsa. Before, I can run alsamixer and "cat /proc/asound/version" will display the version info. Now, it's all gone. 

So I try to recompile the alsa. And for alsa 1.0.23, i just get wrong message when "make" the dirver. For alsa 1.0.24, everything is okay when compiling. But the result is always the same. /proc/asound does not exist and run alsamixer gives a message that says no such file. When I run alsaconf, I just get 

ERROR: modinfo: could not find module snd-opl3sa2
ERROR: modinfo: could not find module snd-cs4236
ERROR: modinfo: could not find module snd-cs4232
ERROR: modinfo: could not find module snd-cs4231
ERROR: modinfo: could not find module snd-es18xx
ERROR: modinfo: could not find module snd-es1688
ERROR: modinfo: could not find module snd-sb16
ERROR: modinfo: could not find module snd-sb8

The following is my result of "http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh"

[http://www.alsa-project.org/db/?f=5844d6871158dcfef052ef963f7e85fea85639d3](http://www.alsa-project.org/db/?f=5844d6871158dcfef052ef963f7e85fea85639d3)

Anyone can help? thanks~~:D

---

### Post by debiant on 2011-08-05
Just moved up to 11.04 from 9.04 and I haven't got the sound working yet either!
Have you tried the sound sticky thread? I'm working my way through it now


[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)



:confused:

---

### Post by sliter on 2011-08-06
thanks~~~what says in the link is what I had done before, still worth nothing~~I reinstall my ubuntu~~so now I can work with headphone but still no sound in speakers~~

thanks anyway~~

---

