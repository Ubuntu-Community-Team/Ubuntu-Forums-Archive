---
title: "pulseaudio equalizer"
date: 2010-01-11
forum: General Help
---

### Post by phish3 on 2010-01-11
The main source of information and how to setup is [here]("http://pulseaudio.org/wiki/SystemEqualizer")
For qpaeq, it is recommended you try git versions (listed on the wiki).

(old) Screenshots are available [here]("http://sites.google.com/site/nevion/projects/qpaeq")
Video of equalizing in action (skip to 2:20) [here]("http://www.youtube.com/watch?v=HSiMyJZvdes")


Here is a list of pros/cons for the pulseaudio equalizer vs the ladspa/mbeq backed equalizers (psyche83's eq. script thus included)
pros:
[LIST]
[*]realtime adjustments
[*]unlimited bands* (qpaeq dynamically scales the bands to the width of the window)
[*]higher accuracy
[*]frequencies are natural (mbeq's frequencies are proportional to the real frequencies we hear in)
[/LIST]
*the limit is half the sample-rate of your master sink/sound card. One cannot specify any more useful information beyond that number of bands (theoretical limit).

cons:
[LIST]
[*]general/tradeable presets not implemented yet, slowly being worked on though (server side preset "states" exist though)
[/LIST]

cons with a mbeq backed equalizer:
[LIST]
[*]frequencies (coefficients you specify in control) above it's 1024 hz are ignored
[*]aliasing occurs because the filter doesn't sample sufficiently, see the bottom two graphics [here]("http://www.danbullard.com/dan/aliasing.html") for a  visual description.
[*]frequencies are proportional to the real frequencies we hear in
[/LIST]

cons with [psyche83's gui]("http://ubuntuforums.org/showthread.php?t=1308838") (mbeq backed):
[LIST]
[*]need to hit apply for changes to take effect (not real-time)
[*]fixed to 15 bands
[/LIST]

Also note that this equalizer is in upstream pulseaudio and will be probably be released in the next official version (whenever that is).

---

### Post by towheedm on 2010-01-12
Pulseaudio works properly on my system even with Rythymbox. Did the whole HOWTO Pulseaudio Fixes.

I used pavucontrol to verify that the FFT equalizer was selected as the default sink and that my SoundBlaster was not muted, then daemonized pulseaudio. Opened Rythymbox and got the qpaeq to work. BTW, much much much better quality. However, problem #2 still exists. If I try to resize the qpaeq window, it becomes non-responsive and starts eating memory. I looked at the memory map using the system monitor and saw that the heap was eating all of the memory, looks like a bug in Python to me. qpaeq.py memory usage was quite low. After leaving it for about 15mins, it chewed up all of my physical memory and about 1GiB of swap.

The other thing now is that once I restart and log in, the SoundBlaster is always muted so I have to pavucontrol and unmute it. But once I do this, close pavucontrol, daemonize PA launch qpaeq and open up Rythymbox, there's nice sound. Unfortunately, once I daemonize PA I loose the ability to control the volume with the volume control on my kybd. Any suggestions on these two issues, especially the resizing will be greatly appreciated.

I will try and compile although I have never ever had to before. My only programming experience is with VisualBasic and VBA under Windows. BTW, went into GNOME Alsa Mixer and turned on the 3D Control. PA + qpaeq + 3D = WOW WOW WOW!

Thanks.

Just occurred to me that this eq sounds very similar to the Nevion Eq plugin for WinAmp, same author I'm assuming. :)

Using Karmic with latest updates, P4 2.8GHz 1MiB RAM 2GiB swap.

PS:  I installed GIT using Synaptic. I then followed your instructions in the SystemEqualizer wiki, the following are the results from the clone and checkout GIT commands:
```
towheed@ga1a4ch:~$ git clone git://gitorious.org/pulseaudio-equalizer/pulseaudio-equalizer.git pulseaudio-equalizer
Initialized empty Git repository in /home/towheed/pulseaudio-equalizer/.git/
remote: Counting objects: 37374, done.
remote: Compressing objects: 100% (7696/7696), done.
remote: Total 37374 (delta 30982), reused 35929 (delta 29643)
Receiving objects: 100% (37374/37374), 11.52 MiB | 34 KiB/s, done.
Resolving deltas: 100% (30982/30982), done.
towheed@ga1a4ch:~$ cd pulseaudio-equalizer && git checkout -t origin/master
fatal: git checkout: branch master already exists
```The first command under the Compiling section is ```
cd pulseaudio-equalizer.git
```However there is no pulseaudio-equalizer.git directory.  There is a pulseaudio-equalizer/.git directory.  I'll assume it's a typo and cd to pulseaudio-equalizer/.git.  But then the next command ```
./autogen.sh
``` will not work because there is no such file in the pulseaudio-equalizer/.git directory.  Any advice?
Thanks again.

---

### Post by phish3 on 2010-01-12
I'd discourage the weak at heart from compiling pulseaudio from source. That being said, the pulseaudio-equalizer.git thing is more of a trap than a typo and not all instructions should always be followed to the letter given configuration/system differences...   There are instructions out there for how to compile pulseaudio though and it follows a standard layout & autogen.sh/configure/make  cycle.  In short, you cd'd into the .git directory and need to work a directory above it.

No clue about the 1G bug with qpaeq.  What graphics drivers are you using?  So far you are the first to have it...  I can't fix it if I can't reproduce it.  Hopefully somebody else will fall victim to it.

Regarding pavucontrol, it looks like it might be sufficient to simply close pavucontrol - perhaps no need to restart pulse or anything. I can use my system (kmix) and alsa mixers just fine btw (including w/ media keys).

Interesting coincidence with the winamp plugin, but no - not the same author :-).

---

### Post by towheedm on 2010-01-13
> the pulseaudio-equalizer.git thing is more of a trap than a typo and not all instructions should always be followed to the letter given configuration/system differences... There are instructions out there for how to compile pulseaudio though and it follows a standard layout & autogen.sh/configure/make cycle. In short, you cd'd into the .git directory and need to work a directory above it.OK so I thought that is what I needed to do.  I'm not faint at heart, learn fast and am willing to take the risk if it means learning something new.  Well I'll search for the instructions and give it a try.

My graphics card is the nVidia FX5200 and I'm using the proprietary (Version 173) driver.  I'll uninstall and try with the non-accelerated drivers.  BTW, I ran the lastest qpaeq.py from GIT but the same.  What the last control 'Coda' used for?

Thanks.

I uninstalled the propriety nVidia driver, uninstalled Compiz (just in case) but it still has the resize issue.

---

### Post by phish3 on 2010-01-13
Regarding coda, it is the control point for the last frequency band of the filter and so controls the taper off from the last numbered band to the end (potentially alot of high frequencies in the smaller views)

---

### Post by towheedm on 2010-01-15
So that between the DC and the Coda sliders, I can control the the bandwidth of the eq, correct?

I did some preliminary testing into the resize issue and it seems that the code is stuck in a never ending loop in the create_slider routine.  Hope this helps.

---

### Post by phish3 on 2010-01-15
Please give this branch a try to see if it fixes the problem, if it doesn't, there should be some output to the terminal it is ran from that could be helpful:

[http://gitorious.org/qpaeq/qpaeq/blobs/raw/testing/qpaeq.py](http://gitorious.org/qpaeq/qpaeq/blobs/raw/testing/qpaeq.py)


The bandwidth of the equalizer is fixed, it contains all frequencies between 0 (Where the dc control point lives) and ~half the samplerate of the master sink it is attached to (where the coda control point lives), otherwise known as the nyquist rate. Dc and Coda are the endpoints of the bandwidth range.

---

### Post by Starks on 2010-01-17
Is this available for Lucid's 0.9.22?

---

### Post by phish3 on 2010-01-17
As of right now, no because lucid's using the stable-queue branch and not master.  They'll pick it up automatically as long as pulse cranks an official version out before ubuntu freezes everything... I suppose at this stage one could also ask the ubuntu audio team to include it too.

If a few more people chime in for lucid I might start another repo.

---

### Post by towheedm on 2010-01-19
> **phish3 said:**
> Please give this branch a try to see if it fixes the problem, if it doesn't, there should be some output to the terminal it is ran from that could be helpful:

[http://gitorious.org/qpaeq/qpaeq/blobs/raw/testing/qpaeq.py](http://gitorious.org/qpaeq/qpaeq/blobs/raw/testing/qpaeq.py)


The bandwidth of the equalizer is fixed, it contains all frequencies between 0 (Where the dc control point lives) and ~half the samplerate of the master sink it is attached to (where the coda control point lives), otherwise known as the nyquist rate. Dc and Coda are the endpoints of the bandwidth range.

Nope, qpaeq from the other branch did the same thing.  Note though, I was able to get it to resize while single stepping the code.  You must however single step the resize routine including the routines that recalcs the centre freqs and the no.of sliders.  In my test, variable c iterated about 164 times before redrawing the interface and when it did, there were only 32 sliders, all the same same width as the default eq window size.  But the freqs for the sliders were adjusting according to their freqs.  Could it be a timing issue somewhere in the resize routine since single stepping introduces an inherent delay between line execution.

Also, the resize issue exists even if resizing vertically.  Again, I was able to get the vertical resize to work while single stepping the resize routine.

My screen's resolution is 1280x1024.

Thanks again for a great sounding eq, if only the resize works for me. :(

---

### Post by phish3 on 2010-01-20
Hi again,

I updated the file - could you test again?  It should print alot of debugging output if you do -d on it this time if you still have problems.  I believe I found the cause or at least a related bug. [Same link (here)]("http://gitorious.org/qpaeq/qpaeq/blobs/raw/testing/qpaeq.py")

---

### Post by towheedm on 2010-01-20
OK thanks, this seem to work now.  I can only get 33 sliders though.  Here is the debug output after starting and resizing to the max width of my screen's roslution (1280), it's kinda long but I included everything.

```
add sliders to fit
old e_w = -1, t_w = 534
evaluating w/ target=534, variable=12, result=484, error=50
evaluating w/ target=534, variable=13, result=520, error=14
evaluating w/ target=534, variable=14, result=556, error=-22
evaluating w/ target=534, variable=13, result=520, error=14
Chose bands=13 with error=14

add sliders to fit
old e_w = 534, t_w = 536
evaluating w/ target=536, variable=13, result=520, error=16
evaluating w/ target=536, variable=14, result=556, error=-20
evaluating w/ target=536, variable=13, result=520, error=16
Chose bands=13 with error=16

add sliders to fit
old e_w = 536, t_w = 608
evaluating w/ target=608, variable=14, result=556, error=52
evaluating w/ target=608, variable=15, result=592, error=16
evaluating w/ target=608, variable=16, result=628, error=-20
evaluating w/ target=608, variable=15, result=592, error=16
Chose bands=15 with error=16

add sliders to fit
old e_w = 608, t_w = 750
evaluating w/ target=750, variable=18, result=700, error=50
evaluating w/ target=750, variable=19, result=736, error=14
evaluating w/ target=750, variable=20, result=772, error=-22
evaluating w/ target=750, variable=19, result=736, error=14
Chose bands=19 with error=14

add sliders to fit
old e_w = 750, t_w = 821
evaluating w/ target=821, variable=20, result=772, error=49
evaluating w/ target=821, variable=21, result=808, error=13
evaluating w/ target=821, variable=22, result=844, error=-23
evaluating w/ target=821, variable=21, result=808, error=13
Chose bands=21 with error=13

add sliders to fit
old e_w = 821, t_w = 822
evaluating w/ target=822, variable=21, result=808, error=14
evaluating w/ target=822, variable=22, result=844, error=-22
evaluating w/ target=822, variable=21, result=808, error=14
Chose bands=21 with error=14

add sliders to fit
old e_w = 822, t_w = 873
evaluating w/ target=873, variable=22, result=844, error=29
evaluating w/ target=873, variable=23, result=880, error=-7
evaluating w/ target=873, variable=22, result=844, error=29
Chose bands=22 with error=29

add sliders to fit
old e_w = 873, t_w = 973
evaluating w/ target=973, variable=24, result=916, error=57
evaluating w/ target=973, variable=25, result=952, error=21
evaluating w/ target=973, variable=26, result=988, error=-15
evaluating w/ target=973, variable=25, result=952, error=21
Chose bands=25 with error=21

add sliders to fit
old e_w = 973, t_w = 1099
evaluating w/ target=1099, variable=28, result=1060, error=39
evaluating w/ target=1099, variable=29, result=1096, error=3
evaluating w/ target=1099, variable=30, result=1132, error=-33
evaluating w/ target=1099, variable=29, result=1096, error=3
Chose bands=29 with error=3

add sliders to fit
old e_w = 1099, t_w = 1129
evaluating w/ target=1129, variable=29, result=1096, error=33
evaluating w/ target=1129, variable=30, result=1132, error=-3
evaluating w/ target=1129, variable=29, result=1096, error=33
Chose bands=29 with error=33

add sliders to fit
old e_w = 1129, t_w = 1130
evaluating w/ target=1130, variable=29, result=1096, error=34
evaluating w/ target=1130, variable=30, result=1132, error=-2
evaluating w/ target=1130, variable=29, result=1096, error=34
Chose bands=29 with error=34

add sliders to fit
old e_w = 1130, t_w = 1205
evaluating w/ target=1205, variable=30, result=1132, error=73
evaluating w/ target=1205, variable=31, result=1168, error=37
evaluating w/ target=1205, variable=32, result=1204, error=1
evaluating w/ target=1205, variable=33, result=1240, error=-35
evaluating w/ target=1205, variable=32, result=1204, error=1
Chose bands=32 with error=1

add sliders to fit
old e_w = 1205, t_w = 1210
evaluating w/ target=1210, variable=32, result=1204, error=6
evaluating w/ target=1210, variable=33, result=1240, error=-30
evaluating w/ target=1210, variable=32, result=1204, error=6
Chose bands=32 with error=6

add sliders to fit
old e_w = 1210, t_w = 1210
evaluating w/ target=1210, variable=32, result=1204, error=6
evaluating w/ target=1210, variable=33, result=1240, error=-30
evaluating w/ target=1210, variable=32, result=1204, error=6
Chose bands=32 with error=6

add sliders to fit
old e_w = 1210, t_w = 1210
evaluating w/ target=1210, variable=32, result=1204, error=6
evaluating w/ target=1210, variable=33, result=1240, error=-30
evaluating w/ target=1210, variable=32, result=1204, error=6
Chose bands=32 with error=6

add sliders to fit
old e_w = 1210, t_w = 1210
evaluating w/ target=1210, variable=32, result=1204, error=6
evaluating w/ target=1210, variable=33, result=1240, error=-30
evaluating w/ target=1210, variable=32, result=1204, error=6
Chose bands=32 with error=6

add sliders to fit
old e_w = 1210, t_w = 1211
evaluating w/ target=1211, variable=32, result=1204, error=7
evaluating w/ target=1211, variable=33, result=1240, error=-29
evaluating w/ target=1211, variable=32, result=1204, error=7
Chose bands=32 with error=7

add sliders to fit
old e_w = 1211, t_w = 1212
evaluating w/ target=1212, variable=32, result=1204, error=8
evaluating w/ target=1212, variable=33, result=1240, error=-28
evaluating w/ target=1212, variable=32, result=1204, error=8
Chose bands=32 with error=8

add sliders to fit
old e_w = 1212, t_w = 1197
evaluating w/ target=1197, variable=31, result=1168, error=29
evaluating w/ target=1197, variable=32, result=1204, error=-7
evaluating w/ target=1197, variable=31, result=1168, error=29
Chose bands=31 with error=29

add sliders to fit
old e_w = 1197, t_w = 1204
evaluating w/ target=1204, variable=31, result=1168, error=36
evaluating w/ target=1204, variable=32, result=1204, error=0
evaluating w/ target=1204, variable=33, result=1240, error=-36
evaluating w/ target=1204, variable=32, result=1204, error=0
Chose bands=32 with error=0

add sliders to fit
old e_w = 1204, t_w = 1247
evaluating w/ target=1247, variable=33, result=1240, error=7
evaluating w/ target=1247, variable=34, result=1276, error=-29
evaluating w/ target=1247, variable=33, result=1240, error=7
Chose bands=33 with error=7

saving state
add sliders to fit
old e_w = 1247, t_w = 1213
evaluating w/ target=1213, variable=32, result=1204, error=9
evaluating w/ target=1213, variable=33, result=1240, error=-27
evaluating w/ target=1213, variable=32, result=1204, error=9
Chose bands=32 with error=9

add sliders to fit
old e_w = 1213, t_w = 842
evaluating w/ target=842, variable=22, result=844, error=-2
evaluating w/ target=842, variable=21, result=808, error=34
Chose bands=21 with error=34

add sliders to fit
old e_w = 842, t_w = 534
evaluating w/ target=534, variable=13, result=520, error=14
evaluating w/ target=534, variable=14, result=556, error=-22
evaluating w/ target=534, variable=13, result=520, error=14
Chose bands=13 with error=14

add sliders to fit
old e_w = 534, t_w = 535
evaluating w/ target=535, variable=13, result=520, error=15
evaluating w/ target=535, variable=14, result=556, error=-21
evaluating w/ target=535, variable=13, result=520, error=15
Chose bands=13 with error=15

add sliders to fit
old e_w = 535, t_w = 555
evaluating w/ target=555, variable=13, result=520, error=35
evaluating w/ target=555, variable=14, result=556, error=-1
evaluating w/ target=555, variable=13, result=520, error=35
Chose bands=13 with error=35

add sliders to fit
old e_w = 555, t_w = 730
evaluating w/ target=730, variable=17, result=664, error=66
evaluating w/ target=730, variable=18, result=700, error=30
evaluating w/ target=730, variable=19, result=736, error=-6
evaluating w/ target=730, variable=18, result=700, error=30
Chose bands=18 with error=30

add sliders to fit
old e_w = 730, t_w = 1151
evaluating w/ target=1151, variable=28, result=1060, error=91
evaluating w/ target=1151, variable=29, result=1096, error=55
evaluating w/ target=1151, variable=30, result=1132, error=19
evaluating w/ target=1151, variable=31, result=1168, error=-17
evaluating w/ target=1151, variable=30, result=1132, error=19
Chose bands=30 with error=19

add sliders to fit
old e_w = 1151, t_w = 1248
evaluating w/ target=1248, variable=32, result=1204, error=44
evaluating w/ target=1248, variable=33, result=1240, error=8
evaluating w/ target=1248, variable=34, result=1276, error=-28
evaluating w/ target=1248, variable=33, result=1240, error=8
Chose bands=33 with error=8

towheed@ga1a4ch:~$ python ~/Desktop/qpaeq.py -d
add sliders to fit
old e_w = -1, t_w = 534
evaluating w/ target=534, variable=12, result=484, error=50
evaluating w/ target=534, variable=13, result=520, error=14
evaluating w/ target=534, variable=14, result=556, error=-22
evaluating w/ target=534, variable=13, result=520, error=14
Chose bands=13 with error=14

add sliders to fit
old e_w = 534, t_w = 563
evaluating w/ target=563, variable=13, result=520, error=43
evaluating w/ target=563, variable=14, result=556, error=7
evaluating w/ target=563, variable=15, result=592, error=-29
evaluating w/ target=563, variable=14, result=556, error=7
Chose bands=14 with error=7

add sliders to fit
old e_w = 563, t_w = 781
evaluating w/ target=781, variable=19, result=736, error=45
evaluating w/ target=781, variable=20, result=772, error=9
evaluating w/ target=781, variable=21, result=808, error=-27
evaluating w/ target=781, variable=20, result=772, error=9
Chose bands=20 with error=9

add sliders to fit
old e_w = 781, t_w = 1205
evaluating w/ target=1205, variable=30, result=1132, error=73
evaluating w/ target=1205, variable=31, result=1168, error=37
evaluating w/ target=1205, variable=32, result=1204, error=1
evaluating w/ target=1205, variable=33, result=1240, error=-35
evaluating w/ target=1205, variable=32, result=1204, error=1
Chose bands=32 with error=1

saving state
saving state
towheed@ga1a4ch:~$ python ~/Desktop/qpaeq.py -d
add sliders to fit
old e_w = -1, t_w = 534
evaluating w/ target=534, variable=12, result=484, error=50
evaluating w/ target=534, variable=13, result=520, error=14
evaluating w/ target=534, variable=14, result=556, error=-22
evaluating w/ target=534, variable=13, result=520, error=14
Chose bands=13 with error=14

add sliders to fit
old e_w = 534, t_w = 537
evaluating w/ target=537, variable=13, result=520, error=17
evaluating w/ target=537, variable=14, result=556, error=-19
evaluating w/ target=537, variable=13, result=520, error=17
Chose bands=13 with error=17

saving state
add sliders to fit
old e_w = 537, t_w = 697
evaluating w/ target=697, variable=16, result=628, error=69
evaluating w/ target=697, variable=17, result=664, error=33
evaluating w/ target=697, variable=18, result=700, error=-3
evaluating w/ target=697, variable=17, result=664, error=33
Chose bands=17 with error=33

add sliders to fit
old e_w = 697, t_w = 1068
evaluating w/ target=1068, variable=26, result=988, error=80
evaluating w/ target=1068, variable=27, result=1024, error=44
evaluating w/ target=1068, variable=28, result=1060, error=8
evaluating w/ target=1068, variable=29, result=1096, error=-28
evaluating w/ target=1068, variable=28, result=1060, error=8
Chose bands=28 with error=8

add sliders to fit
old e_w = 1068, t_w = 1197
evaluating w/ target=1197, variable=31, result=1168, error=29
evaluating w/ target=1197, variable=32, result=1204, error=-7
evaluating w/ target=1197, variable=31, result=1168, error=29
Chose bands=31 with error=29

saving state
saving state
saving state
saving state
saving state
saving state
add sliders to fit
old e_w = 1197, t_w = 1199
evaluating w/ target=1199, variable=31, result=1168, error=31
evaluating w/ target=1199, variable=32, result=1204, error=-5
evaluating w/ target=1199, variable=31, result=1168, error=31
Chose bands=31 with error=31

add sliders to fit
old e_w = 1199, t_w = 1228
evaluating w/ target=1228, variable=31, result=1168, error=60
evaluating w/ target=1228, variable=32, result=1204, error=24
evaluating w/ target=1228, variable=33, result=1240, error=-12
evaluating w/ target=1228, variable=32, result=1204, error=24
Chose bands=32 with error=24

add sliders to fit
old e_w = 1228, t_w = 1230
evaluating w/ target=1230, variable=32, result=1204, error=26
evaluating w/ target=1230, variable=33, result=1240, error=-10
evaluating w/ target=1230, variable=32, result=1204, error=26
Chose bands=32 with error=26

add sliders to fit
old e_w = 1230, t_w = 1250
evaluating w/ target=1250, variable=32, result=1204, error=46
evaluating w/ target=1250, variable=33, result=1240, error=10
evaluating w/ target=1250, variable=34, result=1276, error=-26
evaluating w/ target=1250, variable=33, result=1240, error=10
Chose bands=33 with error=10

add sliders to fit
old e_w = 1250, t_w = 1250
evaluating w/ target=1250, variable=33, result=1240, error=10
evaluating w/ target=1250, variable=34, result=1276, error=-26
evaluating w/ target=1250, variable=33, result=1240, error=10
Chose bands=33 with error=10

add sliders to fit
old e_w = 1250, t_w = 1250
evaluating w/ target=1250, variable=33, result=1240, error=10
evaluating w/ target=1250, variable=34, result=1276, error=-26
evaluating w/ target=1250, variable=33, result=1240, error=10
Chose bands=33 with error=10

add sliders to fit
old e_w = 1250, t_w = 1250
evaluating w/ target=1250, variable=33, result=1240, error=10
evaluating w/ target=1250, variable=34, result=1276, error=-26
evaluating w/ target=1250, variable=33, result=1240, error=10
Chose bands=33 with error=10

add sliders to fit
old e_w = 1250, t_w = 1250
evaluating w/ target=1250, variable=33, result=1240, error=10
evaluating w/ target=1250, variable=34, result=1276, error=-26
evaluating w/ target=1250, variable=33, result=1240, error=10
Chose bands=33 with error=10

add sliders to fit
old e_w = 1250, t_w = 1250
evaluating w/ target=1250, variable=33, result=1240, error=10
evaluating w/ target=1250, variable=34, result=1276, error=-26
evaluating w/ target=1250, variable=33, result=1240, error=10
Chose bands=33 with error=10

towheed@ga1a4ch:~$ python ~/Desktop/qpaeq.py -d
add sliders to fit
old e_w = -1, t_w = 534
evaluating w/ target=534, variable=12, result=484, error=50
evaluating w/ target=534, variable=13, result=520, error=14
evaluating w/ target=534, variable=14, result=556, error=-22
evaluating w/ target=534, variable=13, result=520, error=14
Chose bands=13 with error=14

add sliders to fit
old e_w = 534, t_w = 535
evaluating w/ target=535, variable=13, result=520, error=15
evaluating w/ target=535, variable=14, result=556, error=-21
evaluating w/ target=535, variable=13, result=520, error=15
Chose bands=13 with error=15

add sliders to fit
old e_w = 535, t_w = 620
evaluating w/ target=620, variable=15, result=592, error=28
evaluating w/ target=620, variable=16, result=628, error=-8
evaluating w/ target=620, variable=15, result=592, error=28
Chose bands=15 with error=28

add sliders to fit
old e_w = 620, t_w = 822
evaluating w/ target=822, variable=19, result=736, error=86
evaluating w/ target=822, variable=20, result=772, error=50
evaluating w/ target=822, variable=21, result=808, error=14
evaluating w/ target=822, variable=22, result=844, error=-22
evaluating w/ target=822, variable=21, result=808, error=14
Chose bands=21 with error=14

add sliders to fit
old e_w = 822, t_w = 832
evaluating w/ target=832, variable=21, result=808, error=24
evaluating w/ target=832, variable=22, result=844, error=-12
evaluating w/ target=832, variable=21, result=808, error=24
Chose bands=21 with error=24

add sliders to fit
old e_w = 832, t_w = 1072
evaluating w/ target=1072, variable=27, result=1024, error=48
evaluating w/ target=1072, variable=28, result=1060, error=12
evaluating w/ target=1072, variable=29, result=1096, error=-24
evaluating w/ target=1072, variable=28, result=1060, error=12
Chose bands=28 with error=12

add sliders to fit
old e_w = 1072, t_w = 1252
evaluating w/ target=1252, variable=32, result=1204, error=48
evaluating w/ target=1252, variable=33, result=1240, error=12
evaluating w/ target=1252, variable=34, result=1276, error=-24
evaluating w/ target=1252, variable=33, result=1240, error=12
Chose bands=33 with error=12

```Again, thanks a million.:D

---

### Post by diddy1234 on 2010-01-26
This sounds like great work.

For me,at the moment I will stay using 'psyke83' package as it is easy to install. ([http://ubuntuforums.org/showthread.php?t=1308838](http://ubuntuforums.org/showthread.php?t=1308838))

As a tip could I recommend that we bear in mind desktop space for us netbook users (mostly running at 1024 x 600).
I don't fancy having 100 od bands for adjustment when my desktop would not show all of them but then only 7 bands would be poor (if you understand what I mean).

Still great work.

Any news on installable deb files ?

---

### Post by NRDNick on 2010-01-31
I just wanted to say thank you for your work involved with this. The PPA made things quite simple, though it took me a lil while to figure out how to compile/install the qpaeq (sorry I'm still a noob when it comes to compiling); Once I added the eq sink to my default.pa the program loaded fine and I could stretch the eq across my screen (1680*1050) netting me 44 eq channels :) I can now actually hear sounds in the low range when I listen to music! I did notice some scratching/overdriving on certain programs like Mumble, I got around this by setting my main sink as my sound card w/o the EQ on it, then using the pulseaudio volume control to manually choose the eq sink for Rhythmbox. I don't know why Rythmbox can handle the eq sink and mumble can't, but I'm not complaining.  I suppose I should start a separate thread on the matter. Either way, thanks again for this!

---

### Post by Starks on 2010-03-03
I'll ask again why it is more important that Karmic gets an equalizer PPA while Lucid gets no PPA and an unreasonable "no" from ubuntu audio dev to even the idea of including it in Lucid when currently released versions already support it.

---

### Post by phish3 on 2010-04-15
Starks,

sorry for the late reply, I'll get around to the lucid ppa soon I hope.  The audio dev members mentioned to me they'd provide it in their ppa or a sister ppa some months ago, but that hasn't happened. 

As for the next release not having it by default... while I sympathize with it being an LTS release and needing to be as stable as can be... it's just a runtime optional module... this is the kind of logic that chases me away from a distro :(.

---

### Post by Bastanteroma on 2010-05-20
Any chance you've had time to get around to a Lucid PPA for this, phish3?

---

### Post by jobarjo on 2010-05-25
Hi

I tried to compile the equalizer in fedora12 following your instructions on the pulseaudio wiki.
The makefile finished succesfully.
But I then tried a fake install and saw it wanted to install these files:
libpulsecommon-0.9.19.la libpulse.la libpulse-simple.la libpulse-browse.la libpulse-mainloop-glib.la libpulsedsp.la libpulsecore-0.9.19

In fedora12, pulseaudio is 0.9.21
How can I fix this?
Is it in the configure? or the version is hardcoded?

Thanks

---

### Post by Grone1985 on 2010-07-04
Is there a way to try this on Lucid? Thanks! BTW Great work!!

---

### Post by Grone1985 on 2010-07-15
Bump:D

---

### Post by jayseye on 2010-08-30
> **phish3 said:**
> If a few more people chime in for lucid I might start another repo.

+1 for a Lucid repo
 
Thanks!

---

### Post by oldos2er on 2010-08-30
Already is one: [http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/](http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/)

---

### Post by deankovell on 2010-11-17
+1 for maverick
and thanks for the time you've already put into this phish3

---

### Post by k7k0 on 2010-12-13
> **deankovell said:**
> +1 for maverick
and thanks for the time you've already put into this phish3
For maverick try this:

```

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install pulseaudio-equalizer

```
[http://www.ubuntuupdates.org/ppa/webupd8?dist=maverick](http://www.ubuntuupdates.org/ppa/webupd8?dist=maverick)

---

### Post by jangirke on 2011-09-28
@k7k0
one repo is missing for 10.04
here is the complete code snipet:
```

sudo su
add-apt-repository ppa:psyke83/ppa
add-apt-repository ppa:nilarimogard/webupd8
apt-get update && apt-get install pulseaudio-equalizer

```And here are some files that might work for other people:
[http://www.mediafire.com/?y2pvv2macusm9](http://www.mediafire.com/?y2pvv2macusm9)

I found it somewhere in the web.
):P
PS: Mail me if the link is dead
[email]jangirke@gmail.com[/email]

---

### Post by oldos2er on 2011-09-28
Closed for necromancy.

---

