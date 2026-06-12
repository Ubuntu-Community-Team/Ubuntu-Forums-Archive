---
title: "ATI and NVIDIA comparison. This is bad?"
date: 2010-09-09
forum: General Help
---

### Post by Glaucous on 2010-09-09
Following setup:
AMD Phenom 2 x4 940
8 GB RAM
Kubuntu 10.04 x 64, KDE 4.5.

I have been using ATI HD4870 for a while using Kubuntu, and my performance has been somewhat unreliable. World of Warcraft in Wine was playable, but still very bad. OpenGL performance in my test-game, playing around with particles, was okay.
Now I'm testing NVIDIA GTX260, and wow, there sure is a difference. The graphics cards are similar in performance (on Windows and so on), although HD4870 is a bit better. First a few numbers:

**fgl_glxgears:**
~2200 FPS - ATI
~2100 FPS - NVIDIA

**glxgears:**
~44 000 frames / 5 sec - ATI
~39 000 frames / 5 sec - NVIDIA

As you can see, simple OpenGL effects are working well and shows that the ATI card is a bit better - which it should.

**World of Warcraft Wine:**
~20-35 FPS Lowest Graphics - ATI
~50-60 FPS (Almost) highest graphics - NVIDIA

And there we have a big difference, o'boy. This is the same FPS as I get in Windows (but using ATI). Although WoW is known to favor NVIDIA over ATI, I do not think it should make this big of a difference, especially since it's running under Wine.

**OpenGL particles (simple test)**
~30k particles (20-30 FPS) - ATI
~90k particles (50-60 FPS) - NVIDIA

This game is composed of SFML and OpenGL 2.0. As you can see, the performance is quite different. The performance overall when testing this game was better, less spikes in FPS, smoother.

Overall is V-sync and composition working better with NVIDIA as well.

Tested drives on ATI:
10.4, 10.6, 10.7, 10.8.

It should also be noted that performance on Windows XP/Vista/7 was very good with my ATI HD4870. And direct rendering was of course enabled.

Do these numbers even look "real"? I mean, did I fail on a whole new level when installing and configuring ATI drivers (multiple times)? I can almost assure you that I installed them properly.
I've read around on many forums that ATI drivers apparently aren't the best out there on Linux.

Right now I'm considering buying a NVIDIA graphics card, only because of the drivers. Do anyone else of you have any experience with ATI cards and NVIDIA cards?

Keep it constructive people, no flame wars. ;)

---

### Post by 3Miro on 2010-09-09
I have a Radeon 4850 and I cannot get anything useful to run on it under Linux. The problem is with the driver, ATI drivers for 4xxx series are simply a disaster (even worse for older cards). Nvidia on the other hand has always had good Linux support.

Currently there is no ATI anymore, ever since AMD took over, there has been great improvements in the Linux support, the problem is that the company had a late start and is behind. Thins will change now with the new cards. AMD just released a new FOSS driver for Radeon 5xxx video cards.

PS glxgears is not any kind of a benchmark, they are only a test to see if you can get something to work or not. WoW is more of a benchmark, however, due the historically better Nvidia support for Linux, wine is nv oriented. I don't know about the particles.

---

### Post by Glaucous on 2010-09-09
Wasn't aware that Wine is NVIDIA oriented, but it makes sense I guess.
I know glxgears isn't a benchmark, but it does show me something at least.

Downloading Unigine Heaven, going to see what happens there. Anyhow, there's isn't really any need to benchmark anything else - it already clearly shows that the NVIDIA drivers are handling it better.

Now with ATI 6xxx series around the corner it'd be great if they could push out some nice drivers. Especially since the power usage has been reduced.

Edit3: It seems like Unigine Heaven proved me wrong. glxgears is worthless (yes you were right) and Wine is very NVIDIA optimized.

NVIDIA GTX 260
FPS:
36.1
Scores:
910
Min FPS:
19.6
Max FPS:
72.8

ATI HD 4870
FPS:
38.0
Scores:
957
Min FPS:
12.9
Max FPS:
78.5

Unigine Heaven settings:

```
export LD_LIBRARY_PATH=./bin:$LD_LIBRARY_PATH
./bin/Heaven_x64    -video_app opengl \
                    -sound_app openal \
                    -extern_define RELEASE \
                    -system_script heaven/unigine.cpp \
                    -engine_config ../data/heaven_2.1.cfg \
                    -console_command "gl_render_use_arb_tessellation_shader 0 && render_restart" \
                    -data_path ../ \
                    -video_fullscreen 1 \
                    -video_mode -1 \
                    -video_width 1680 \
                    -video_height 1050
```

---

