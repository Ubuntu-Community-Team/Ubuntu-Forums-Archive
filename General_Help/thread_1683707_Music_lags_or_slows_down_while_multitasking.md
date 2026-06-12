---
title: "Music lags or slows down while multitasking"
date: 2011-02-07
forum: General Help
---

### Post by yojoe on 2011-02-07
I have a problem multitasking in ubuntu. all i want to do is be able to browse the web or play a game while listening to music, currently trying to do this slows or makes music lag.
I have a dual core processor and 2 gb of ram, and ubuntu runs lightening fast, even while multitasking everything but the music runs great. i can do this in windows, so i dont see why i cant do it in ubuntu.
i have watched my cpu and ram monitors while doing this and there are plenty of unused resources, i believe neither processor core ever tops 20% while trying to do this, and ram, 7%. I want ubuntu to use the extra resources instead of taking away from my music playback. And what i mean by games are like quadrapassel and simple stuff, im not trying anything difficult. So my question is; Can i make ubuntu use more resources, or never sacrifice music quality? i dont see why not... Someone please get back to me on this, it is very important to me. Thankyouinadvance

---

### Post by ellgor on 2011-02-08
Hi,

I play online poker and listen to my music at the same time, single core Amd 3200+, with no prblems, I do use either Mplayer or Vlc to play the music as I found other apps weren't up to the task.

Regards, Ellgor.

---

### Post by yojoe on 2011-02-08
> **ellgor said:**
> Hi,

I play online poker and listen to my music at the same time, single core Amd 3200+, with no prblems, I do use either Mplayer or Vlc to play the music as I found other apps weren't up to the task.

Regards, Ellgor.
I dont have any trouble playing card games or online flash games while listening to music, just anything with constant movement, and I've tried doing it with mplayer and vlc, but they slow down as much as rhythmbox. In windows i can play gta san andreas on the highest visual setting and music in the game is smooth, and i dont have trouble playing any other games while listening to music, i think its because wmp is resource hungry, and wont give up resources to other programs, so they take advantage of extra processing power. Ubuntu runs at like 20% on both cores when i play games but the music slows down.

---

### Post by war.ace on 2011-02-08
My computer also slows down when I listen to music and multi task. I use the app called Audacious to listen to my music. My computer seems to slow down when I have openoffice Word and firefox or Teamspeak 3 open. it's very annoying trying to listen to the music and it starts to loop or freeze

---

### Post by yojoe on 2011-02-08
> **war.ace said:**
> My computer also slows down when I listen to music and multi task. I use the app called Audacious to listen to my music. My computer seems to slow down when I have openoffice Word and firefox or Teamspeak 3 open. it's very annoying trying to listen to the music and it starts to loop or freeze
I wonder if theres something limiting the amount of cpu programs are allowed to use, and i rarely get over 10% ram. So why dont music programs make use of the resources?:mad:

---

### Post by ellgor on 2011-02-09
Hi again,

Just out of curiosity, have you got the absolute latest drivers for your graphics/soundcard, usually both are on the same card, I did find with mine that the provided drivers were not upto the task (did the job,just) it even improved the sound quality as well?

Regards, Ellgor

---

### Post by yojoe on 2011-02-09
> **ellgor said:**
> Hi again,

Just out of curiosity, have you got the absolute latest drivers for your graphics/soundcard, usually both are on the same card, I did find with mine that the provided drivers were not upto the task (did the job,just) it even improved the sound quality as well?

Regards, Ellgor
I dont have the latest drivers because i cant find the download, i have an ati mobility radeon x1300 graphics card, ive been looking and i will continue to look...

---

### Post by -Inoe- on 2011-04-13
I am having the same problem and I **do** think this is a serious problem :(
I use Ubuntu 10.04 LTS Lucid Lynx on a laptop with:
- Intel Celeron CPU          550  @ 2.00GHz
- 1GB of RAM
- Mobile GM965/GL960 Integrated Graphics Controller
- 82801H (ICH8 Family) HD Audio Controller

Ubuntu updates the driver for Intel graphics automatically, right? Or should I get the driver somewhere else? How about the audio?

Oh, and a bit explanation.
I tried to compare Ardentryst and Nexuiz in full screen mode and windowed mode.
The music lags when I open the game in full screen.
While in windowed mode, it plays without trouble.

I tried Rhythmbox, Deadbeef, and Audacious for the player.

Any help is appreciated.

---

### Post by aeiah on 2011-04-13
> **-Inoe- said:**
> I am having the same problem and I **do** think this is a serious problem :(
I use Ubuntu 10.04 LTS Lucid Lynx on a laptop with:
- Intel Celeron CPU          550  @ 2.00GHz
- 1GB of RAM
- Mobile GM965/GL960 Integrated Graphics Controller
- 82801H (ICH8 Family) HD Audio Controller

Ubuntu updates the driver for Intel graphics automatically, right? Or should I get the driver somewhere else? How about the audio?

Oh, and a bit explanation.
I tried to compare Ardentryst and Nexuiz in full screen mode and windowed mode.
The music lags when I open the game in full screen.
While in windowed mode, it plays without trouble.

I tried Rhythmbox, Deadbeef, and Audacious for the player.

Any help is appreciated.

are you using pulseaudio? does it report any errors?

---

### Post by -Inoe- on 2011-04-13
> **aeiah said:**
> are you using pulseaudio? does it report any errors?
Changing the settings in gstreamer-properties seems doing nothing, I didn't notice any difference in Rhythmbox using different plugins, even OSS.
I tested Pulseaudio, ALSA, and OSS in Deadbeef and Audacious.
Using OSS is OK, the music doesn't lag, but it blocks the sound from any other applications, so I don't think of it as a solution.

The music only lags when I am:
- opening the game (full screen),
- closing the game (full screen), and
- switching the game from full screen to windowed mode
- switching the game from windowed to full screen mode

While playing (with or without the sound from the game), the music plays fine.

---

