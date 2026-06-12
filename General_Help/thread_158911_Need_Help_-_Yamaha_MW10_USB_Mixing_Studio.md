---
title: "Need Help - Yamaha MW10 USB Mixing Studio"
date: 2006-04-11
forum: General Help
---

### Post by Todd Tomlinson on 2006-04-11
I just bought a Yamaha MW10 sound mixer with a USB connection and I can't find where I can set that device as the default sound input on my Ubuntu Dapper install.   I have Audacity set up - I can see the sound from my Microphone lighting up the leds on the mixer but I'm not getting any sound on my laptop.   HELP -- how do I specify it as the default input sound device???

---

### Post by Todd Tomlinson on 2006-04-15
Ok -- I solved it -- with a lot of gnashing of teeth and pouring over postings for the past two days.   For anyone else struggling with getting audio input devices working:

1)  Use kmix (a mixer utility) to select the default input device.   In my case I'm using a Compaq laptop running Drake and had two options -- a USB codex or the onboard Intel ICH6 setting.    I first tried the USB codex since the soundboard is connected to my laptop through a USB port.  Wrong choice.   One I selected the Intel ICH6 I was able to finally get it working. If you don't have kmix use apt-get install kmix

2)  I'm using Audacity as my recorder and editing tool.   Its great and easy to use/figure out.
Download and install Audacity.  

3)  In Audacity use edit -> preferences and select the /dev/dsp1 as the input device and then start recording!

After about 20 hours of frustration its finally working.   Now on to my newfound career!

---

