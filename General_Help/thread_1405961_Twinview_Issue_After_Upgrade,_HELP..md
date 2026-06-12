---
title: "Twinview Issue After Upgrade, HELP."
date: 2010-02-13
forum: General Help
---

### Post by Gorbayov on 2010-02-13
well
yesterday i upgraded kubuntu
it upgraded kde to 4.4 and the kernel to 2.6.31.19
installed the NVIDIA driver again (185.18.14, newer drivers breaks twinview completely(even prior upgrade))
after the upgrade i couldn't see my mouse pointer but it worked cause when i moved it and clicked the buttons i could see it works and i just couldnt see it.
i tried to fix it and i than realized that it didnt finish upgrade, so i apt-get upgrade again.
after that my mouse got back.
but now i have a different problem
my twinview setup broke..
if i set twinview from the nvidia-setting tool its working but the second screen (tv) screen is black, no plasma desktop on the second screen, i can only drag windows to it but no maximize, no panel no nothing, if i right click nothing happens, and i cant put plasmoids on it.
primary screen is fine..

today i tried to change some xorg.conf settings
and i found out that it works perfect if i set it to twinview in xorg.conf
i dont want this option turned on when im just starting my pc (the second screen is my tv)
i tried to set twinview to clone in xorg.conf and the clone is working fine but when i set it to side by side in nvidia-settings i have the same problem as i mentioned before with no plasma desktop working on the second screen and i cant maximize (i want to see movies on the tv)

now i have no option but to leave it twinview from the start.


this issue wasn't present before the upgrade, i dont know if its the kernel or the new kde, i guess its the kde upgrade, please help

---

### Post by Gorbayov on 2010-02-13
no one??  :confused: :confused: :confused:

---

### Post by a2z on 2010-02-13
> **Gorbayov said:**
> no one??  :confused: :confused: :confused:

Not sure if this applies to you but try 190 driver. 
I think there is 195 out too. Yea I have 195 but am running 190. 
190 is in synaptics
I think 195 came from an update package. Try updating? I did notice karmic is recommending 195

---

### Post by Gorbayov on 2010-02-14
anything newer than 185 breaks my s-video out completely (in windows 7 and xp too)

---

### Post by Virnik on 2010-02-15
its not problem of nvidia driver. I am using 195 for a two weeks without any problem. the problem is KDE 4.4.
yeah, I did the same misstake as you, upgrading karmic to KDE 4.4 was really wrong turn. Graphic is ok, it looks nice, but blackout with the second monitor really turns me on the chair. another problem is, that maximized windows in the xinerama or twinview mode remembers secodary monitor size, not primary one's, so if you have second monitor plugged in and enabled, maximized windows on primary screen follows secondary's monitor width.

really annoying.
I suppose problem is with missing "Activity Desktop View" (I dunno how it is named in english, I got everything in my czech locale) menu (right click on desktop, unlock widgets, and then again) is missing on the second screen at all. Can this be the problem?

also, what comes to hand with KDE 4.4, did you tried yesterday's upgrade?
python-kde4 and python-qt4 packages has been upgraded, without upgrading dependences. apt in this case, when updates for dependeces does not exist, removes everything what collides with it, so I ended up with removed plasma, KDE, and such.

It took me almost half hour, to get everything fixed again (nah, manual download of few packages, -nodeps remove of each problem package, then install older version, and such), only to find out, that this problem has been fixed 10minutes after my final restore...

I just want to say, that if you already didn't upgraded to KDE 4.4, DO NOT DO IT. it is as unstable as KDE 4.1 was in it's times. If you already upgraded, not using second monitor, and if you are ok with it, think twice before any manual upgrade, or even dist-upgrade. it can be dangerous.

---

### Post by Gorbayov on 2010-02-15
Virnik i totally understand you
not being able to use twinview like i want is annoying..

but i found a little solution as i wrote before
if you configure xorg.conf to start in twinview mode automatically its working good, than i disable twinview in nvidia settings and enable it only when i need to..

but after all i dont want it to start automatically

---

