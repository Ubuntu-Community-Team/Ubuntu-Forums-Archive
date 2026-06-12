---
title: "Using Web Cam and Audio For It in Ubuntu"
date: 2009-09-16
forum: General Help
---

### Post by craig10x on 2009-09-16
Hi:  I have Ubuntu 9.04 on my relatively new Toshiba Laptop (bought earlier this year)....i completely removed Windows from the computer and 100% Ubuntu (and love it...lol)....

All the Hardware has worked great, right off the bat....just one thing though....my laptop has a web cam camera with the audio (mic) function as well...How do i use that in Ubuntu?  

I'm clueless:confused:     ....does Ubuntu need to have something added to use it, or does it work out of the box?  Where should i look for the camera in ubuntu?  what if it doesn't work or i have no audio on it?

Feedback will be most appreciated...Thank You :)

---

### Post by loosie on 2009-09-17
I too have the same question, tho it's not a laptop or built in webcam - it's a USB plug in that I can't get working.

---

### Post by P4man on 2009-09-17
On a laptop the audio and webcam probably have nothing to do with each other. The microphone is connected (internally) to your soundcard. The webcam, is a different device, USB most likely.

Do you need drivers? Usually not.  An easy way to check if the webcam is working is running "cheese" or any other webcam program from the repo's. More info here:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

To test the microphone, check if its set as properly  in system > prefences > sound, then test it with "sound recorder".

If it doesnt work, post the ouput of 

```
lsusb
```

```
lspci
```

---

### Post by no2498 on 2009-09-20
type 
gstreamer-properties

in the terminal
click video try v4l1 and v4l2

find cheese and wxcam instal them

---

### Post by craig10x on 2009-09-23
Update:  What i did was install "Cheese" from the add/remove programs.....
              
Open opening "cheese" i noticed that the webcam light came on and bingo...there was my image on the screen!  Looked pretty good too....
            
I did a "snapshot" and it worked fine...saves as a jpg which i could then move to my photo folder......
              
Then i tried making a video, because i wanted to see if the sound was working also.....The video came out fine...and there IS audio....but the audio is extremely low.....
              
 I went into the Volume Control and boosted the MIC setting to almost 100%....
and then tried doing another Video in "Cheese"...the sound was a little louder, but still very low...even with turning up the volume on my external speakers to maximum...
              
 My sound settings are great for Rhythmbox, Streaming Videos, etc...
  Any ideas on how i can get more sound volume from the MICROPHONE????

Added note: I went into the Volume Control...and to PREFERENCES and checked Mic BOOST...now i get a much normal level of audio...but with "feedback" when i playback the video....

I also see  "Capture" and "Capture1" (which are not presently checked)....What do those do?   

And how do i get rid of the feedback..i tried turning the levels down, but still get it.....

---

### Post by craig10x on 2009-09-24
Well..no one had replied...but i did do a little experimenting on my own....what i did was turn on both the "mic boost" and "capture" in the volume control, and adjust the levels...

Now i am getting a normal level of audio, and there is no longer any "feedback" when i play the video....so, looks like that took care of it.... :P

The webcam and mic audio was the only things i wasn't sure if they were working in Ubuntu...now i can see the Ubuntu 9.04 recognizes EVERYTHING on my Toshiba Laptop, which i have had for about 9 months now.....

I originally started with a WUBI 8.10 installation and was so impressed with Linux and Ubuntu, that after a few months, i installed 9.04 and complete wiped windows from the computer...

I am WINDOWS FREE and LOVING IT  ;)

---

