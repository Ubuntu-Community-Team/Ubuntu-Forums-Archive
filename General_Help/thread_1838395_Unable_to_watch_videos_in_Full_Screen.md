---
title: "Unable to watch videos in Full Screen"
date: 2011-09-03
forum: General Help
---

### Post by rmcellig on 2011-09-03
I just installed Ubuntu 11.04 on my iMac dual boot. When I watch any of my movies/ videos, when I view them full screen in VLC Player, I her the audio but no video. I try in the Movie Player and Movie Player quits right away. What is going on and how can I fix this?

---

### Post by yetiman64 on 2011-09-03
With regard to your attachment, do you have the Unity desktop working Ok? If so you most likely have 3d accelerated drivers in use despite that report. There is a confirmed bug in jockey-gtk (Additional Drivers) that reports the drivers are not in use when they actually are [[COLOR=Blue]--link to bug report--[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788").

Your problem is quite possibly not related to that information, though I'm not sure where you could start looking with regard to the actual problem you report, just some information for you to keep in mind while looking into it.

---

### Post by rmcellig on 2011-09-03
I am using Ubuntu Classic mode. I was wondering if there might be additional software I didn't install?

---

### Post by yetiman64 on 2011-09-03
> **rmcellig said:**
> I am using Ubuntu Classic mode. I was wondering if there might be additional software I didn't install?
With those drivers installed can you load the Unity desktop? That is, do you choose to use Classic or are you forced to ?

If you used the Additional drivers option to install the nvidia drivers you shouldn't need to install any other software to get a 3d environment. 

Codecs like the restricted extras package and libdvdcss2 will be need to be added for playback of various filetypes (particularly for commercial dvds etc). Have you put these in ?

---

### Post by rmcellig on 2011-09-23
What is the code for me to install these drivers so I can paste it into the command line and see if it works. Thanks!!

---

### Post by yetiman64 on 2011-09-23
> **rmcellig said:**
> What is the code for me to install these drivers so I can paste it into the command line and see if it works. Thanks!!

Firstly the drivers:
According to the first attachment you posted you *_have the drivers installed already_* (but showing as not in use, I expect is related to the bug I previously linked to - my post #2) 

I need to know from you the situation,

1. > With those drivers installed can you load the Unity desktop?That is...

> ...do you choose to use Classic or are you forced to ? possibly by a driver related problem.

Secondly the codecs etc I mentioned:
```
sudo apt-get install ubuntu-restricted-extras
``` gives playback for a lot of non-free codecs etc.

Medibuntu (includes libdvdcss2 for commercial dvd playback etc) [[COLOR=Blue]--info link--[/COLOR]]("https://help.ubuntu.com/community/Medibuntu") -- good for dvd, "non-native media formats" etc. Full installation instructions in the link.

Installing the restricted-extras & Medibuntu and its packages from that link should take care of most codec related (non-driver related) issues involved for you hopefully.

---

