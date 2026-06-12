---
title: "No Sound - New Build - Realtek ALC889A"
date: 2010-03-23
forum: General Help
---

### Post by SolitaryMan1941 on 2010-03-23
Hello, I am a brand newbie looking for some *basic* assistance. I have recently completed my first self build. I cannot get any sound. I have a Gigabyte MA785GM-US2H motherboard and intend to run sound through the on-board sound card (Realtek ALC889A). Here is what I have done so far:

1. I have installed the codec provided through the Realtek website

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)


From the terminal:

cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC889A

2. I have made sure nothing is muted (via the alsamixer).

3. I have restarted the computer just to make sure everything installed correctly.

Additional Info:
I have speakers that receive output data from a television. Currently, I have an audio chord running from the green audio jack in the back of the pc to the appropriate jack in the TV for sound (it works with my laptop). Two notable differences between the laptop and the self build: 1. Laptop = VGA, Self Build = DVI-HDMI; 2. Laptop = HP w/ Vista, Self Build = Ubuntu 9.10.

Any ideas for the next course of action? Gratitude in advance for any and all assistance.

---

### Post by SolitaryMan1941 on 2010-03-24
New information same issue:

I have added multiple g streamer plug-ins but still no sound.

---

### Post by fysicsandpholds on 2010-05-08
I am having the same exact problem except all I have is the speakers built into my mac
I have the realtek ALC889A codec installed
I have the ALC889A sound card.
it is very frustrating!

---

### Post by lidex on 2010-05-08
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1302296]("http://ubuntuforums.org/showthread.php?t=1302296")

For karmic also work through this page to eliminate the known audio problems:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

