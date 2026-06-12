---
title: "Installing and using ePSXe"
date: 2010-03-09
forum: General Help
---

### Post by Midnight Star on 2010-03-09
I was following the instructions here to install the ePSXe emulator, and noticed it needed 3 gtk libraries (if you look the last post of that thread, you'll see the 3 that are required to run it). I'm currently using 9.10 Ubuntu Karmic, and wonder if I use the following:

> Solution for those running 64 bit for whom epsxe reports: 

"error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory"

Before/After running one of the generously provided install scripts, get the following three packages

[http://packages.ubuntu.com/en/jaunty/libgtk1.2-common](http://packages.ubuntu.com/en/jaunty/libgtk1.2-common)
[http://packages.ubuntu.com/en/jaunty/libglib1.2ldbl](http://packages.ubuntu.com/en/jaunty/libglib1.2ldbl)
[http://packages.ubuntu.com/en/jaunty/libgtk1.2](http://packages.ubuntu.com/en/jaunty/libgtk1.2)

For libglib1.2ldbl and libgtk1.2, make sure you download the 32 bit (i386) versions. You can then install them as follows:

dpkg -i **[B][B]--force-architecture **[/B][/B]filenameIf that would configure my system to use outdated drivers by default, or would it just install them without using them unless called by a program like ePSXe.

So my question would be about installing outdated libraries, not so much about ePSXe itself.

---

### Post by Midnight Star on 2010-03-10
Does anyone have any idea about installing deprecated libraries?

---

### Post by Th3_Matr1x_Has_Y0u on 2010-03-10
IMHO pSX is a better choice. ;) - DAn

---

### Post by Midnight Star on 2010-03-11
Thanks DAn,

Just gave that a whirl this evening: looks good. It seems the only problem i'm having with it is sound. Which, I think over time will get resolved. The Audio plugin by default uses ALSA, but the sounds still really choppy and sputters, so it might still be invoking Pulse somewhere along the way, not sure.

Any ideas on the best configuration for it? I'm using the defaults.

---

### Post by Th3_Matr1x_Has_Y0u on 2010-03-11
Hi there. Yeah that is a downside to pSX..I've had numerous headaches trying to rememdy the sound situation, with regard to pulseaudio... ;). So much so that i actually tried out a number of other playstation emualtors like epsxe, but in the end came back to pSX, as it seemingly recreates the playstation most accurately and with as least messing about with variables as possible.

 Killing pulseaudio is a bit of a headache, and i think the results are negligible for pSX but it works amazingly well for zsnes (good snes emulator).
To kill pusleaudio i think and dont quote me on this you need to navigate to etc/pulse and find the client.conf file, you then need to open a text editor and change autospawn = yes to autospawn = no. (As i vaguely recall its probably read only attributed, so "sudo nautilus" may come in handy in order to edit file). 

Then just type pulseaudio -k to kill pulseaudio and pulseaudio -D to give it a pulse again (haha sorry lame i know couldn't resist).

As i said running karmic, i haven't really needed to use the whole kill pusleaudio thing, as i haven't really had any problems with it/used to the mild annoyance of it, and if there is any positive effect from cancelling it, it is absolutely negligible with pSX. I found the best thing to speed up sound (so it doesnt skip bloody annoyingly) was to reduce window size particularly for fmv video's (to minimal window size), and then blap it back up to full for playing the game. When running the game if the skippyness is too annoying, you can kill the XA sound by using whichever key you have assigned to reducing XA volume to zero. It's usually only background sorta sounds/music and is usually perfectly playable without it anyways....Like i say i haven't managed to find a compete fix for this emulator (pSX) yet and i did spend a fair while messing with various things.  It usually printed "buffer underrrun" on the terminal screen whenever it skipped, so i tryed installing a real-time kernel assuming it may help with real-time processing of sounds and thus reducing latency, but meh didnt seem to work. Just out of curiosity what system are you running it on specs wise? Mine is a 1.6Ghz atom processor, 1GB Ram, with standard fairly crappy intel graphics milarkee samsung n130 netbook. You can increase the latency on both XA and regular sound in the options, although again for me at least the effect was no different once past a certain point anyways. You can detach the video or whatever setting it is (i forget) and the sound runs fine, but the video is jerky as hell which is pointless. I think its to do with the onboard soundcard probably being fairly crap and not being able to actually process the info quick enough, thus causing stuttering. Or perhaps it could be the programming of the actual emulator, not being economic enough with the processing it is required to do. 

If you manage to get it working fine/no problemos give mea s hout man cos i would fricking love to know what you did! ;). Other than that it does appear to be IMHO anyways, the best playstation emualtor out there. Perhaps the reason the sound is stuttery on mine at least is because its not a good enough system to run it properly, i wouldnt of thought that was the case, but meh you never know. 


- Dan

---

### Post by Midnight Star on 2010-03-12
Hey! I haven't really got into testing much, as i've been working on my music library. But from what I was able to do "out of the box", the video seems to just fine, and the sound goes along great with the game play. It seems to get way outta whack while playing the FMV(s) - like the timing isn't tied as much to the video, as it is to processor speed.

The really weird thing I noticed, is that after killing, changing settings, restarting, then killing and resetting back to the default, the opening FMV's sound is synced back up. 

My system is:

Asrock mobo (not sure on the model, got it for like $25 at Geeks)
1.8g AMD Sempron 3000+ SPU
1g RAM.
nVidia 6600 graphics card (512meg gpu memory).

Give me a bit, and i'll see what I can come up with, then post the results.

---

### Post by Midnight Star on 2010-03-17
Ok, so far it seems to work pretty good. It really depends on the game being played. Something simple like Spyro, pulls off without a hitch, while a later game like Legacy of Kain: Soul Reaver, seems to be plagued with "locks up" during the first level or two. I'm guessing that later games are doing some kind of hardware "trick" to pull something off, and the emulator isn't quite taking that into account.

Later this week i'll try testing something like Parasite Eve II, or RE:2. I'm cusrious how it'll handle a "disc swap" mid game.

Sound was ok, but still has some problems; it's not accurately represent the sounds of the game. I'm not sure if this is an "os" system level audio problem, or something with the emulator. FPS was good and spot on, except for the first time I tried it. After i'll killed the emu, then restarted it, it seemed to work ok. It's tricky at best. What we need is a terminal that shows us what the emu is thinking, so we can figure out what it think it is, or isn't doing.

---

### Post by gwionn on 2010-07-01
Theres Somthing with all games on my computer, i have all the plugins and bios but the emulator shuts down straight away

im only a newbie at ubuntu but the emulator worked when i had windows.???

---

