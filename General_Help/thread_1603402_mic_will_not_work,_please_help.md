---
title: "mic will not work, please help"
date: 2010-10-22
forum: General Help
---

### Post by milankomadina on 2010-10-22
I tryed evrithing and this is my last hope. this is my first time that i work with Ubuntu. reacently i installed ubuntu 10.10 maverick m. and from the begining i have problem with microfone. it does not work and i do not know what to do or how to enable the mic. my sound card is HDA ATI SB and my sound chip is REALTEK ALC 861. IF YOU HAVE ANY SOLUTION PLEASS HELP. if you nead any other device informationen to solve this problem pleass ask me. thanks in advance.

---

### Post by Frogs Hair on 2010-10-22
Preferences > Sound Preferences > Input Tab if you haven't tried already.

---

### Post by gunsten on 2010-10-22
Is it a built-in mic in a laptop?

---

### Post by milankomadina on 2010-10-22
I tryed all posible combination in sound preferences. 
And to answer the second post:  it is built in microfon, but i tryed also with headphones with microfon and it does not work, i also opend alsamixer from the terminal and it seams that all is good.

---

### Post by gunsten on 2010-10-22
I experienced a crazy problem with my built-in mic. It seems it uses some kind of internal noice reduction algorithm by comparing sounds recorded from left and right channel. Well, the result was that ALL RECORDED SOUND was filtered out. The solution in my case was to turn down one channel slightly in PulseAudio Volume Control (package pulseaudio).

Perhaps it's a longshot, but might be worth a try.

---

### Post by milankomadina on 2010-10-22
ok i menaged to get the mic working. I typed in to terminal 
sudo gedit /etc/modprobe.d/alsa-base.conf
and then in the window that apears i typed 
options snd-hda-intel position_fix=1
click save and restart
NOW I HAVE SOUND BUT WHEN I RECORDE SOMETHING IN PLAYBACK I HEAR SOME NOISES
does anybody have solution to this new problem!!!!!!

---

### Post by milankomadina on 2010-10-22
i tryed to fix that with puls audio volume control but nothing hapens.

---

### Post by milankomadina on 2010-10-22
ok my solution with typing sudo gedit ........ do not work. it is only temporary, after some time ( 1h or 2h ) it goes back to the old state. MY MIC STILL DO NOT WORK, I AM OUT WITH SOLUTIONS. ENYBODY HELP.

---

