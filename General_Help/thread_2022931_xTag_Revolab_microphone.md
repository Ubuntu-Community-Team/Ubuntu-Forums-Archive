---
title: "xTag Revolab microphone"
date: 2012-07-11
forum: General Help
---

### Post by terminal27 on 2012-07-11
I am having trouble to make a USB xTag Revolab works with alsa. If I replace the microphone with a Samson USB then no problem for ffmpeg, otherwise give me error:
alsa (....) cannot set channel count to 2 (invalid argument)
if I arecord -l then:
Card 0: MID(HDA Intel MID), device 0: ALC662 Analog....blablabla...
Card 0: MID(HDA Intel MDI), device 2: ALC662 Analog....blablabla...
Card 1: xTag (Revolabs xTag), device 0: USB Audio
 
so if I do 
avconv -f alsa -i hw:1,0 -acodec libmp3lame [http://localhost:8090.....](http://localhost:8090.....)
then give me the error. If I replace the device with a Samson USB1 then is OK.
I guess the fact that revolab is a 2 way device (with earphone support) could be the reason. Any how to force to only 1 channel? (if that is the problem)
Thanks,

---

### Post by terminal27 on 2012-07-12
Done, finally working.
 
I got it wrong at the alsamixer and wrong at the avconv command during different tests.
Go to alsamixer (sudo alsamixer) and 
select F6 and choose xTag Revolab
Then select F5 [all] otherwise the PCM for capture is hidden (even you see a Mic slider) so make sure you get:
<Speakers><bass><PCM (with CAPTURE on top)><Mic>
unmute by pressing M on the keyboard, turn volume up, and Escape to exit
 
then
sudo avconv -f alsa -ac 1 -i hw:1,0 ...
and now should work. (Mine it does) .
My nxt question would be "Has anyone used xTAg Revolabs with linux"? The device has a microphone (as expected from a microphone) and a earphone set to receive signal to your earphone so it is a two way device. Do you have any idea how to make it work with Ubuntu? either Skype or any other application.
Thanks in advance.

---

