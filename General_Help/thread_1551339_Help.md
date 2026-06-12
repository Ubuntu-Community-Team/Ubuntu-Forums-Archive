---
title: "Help"
date: 2010-08-12
forum: General Help
---

### Post by bender1 on 2010-08-12
can't install sound driver,actually i don't know how:P can u help me?


**** List of PLAYBACK Hardware Devices ****
Home directory /home/bender not ours.
card 0: SB [HDA ATI SB], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Unknown-Demon on 2010-08-12
Alright
Go to terminal and type:
```
aplay -l
```
and post the output here.

---

### Post by bender1 on 2010-08-12
**** List of PLAYBACK Hardware Devices ****
Home directory /home/bender not ours.
card 0: SB [HDA ATI SB], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Unknown-Demon on 2010-08-12
Okay,
From the looks of it you already have a sound card installed but it's not playing.
First off go back to terminal and type:
```
alsamixer
```
And be sure _nothing_ is muted.

---

### Post by bender1 on 2010-08-12
nothing is muted:D i fixed it ,now i have other problem. my Mozilla won't start.can u tell me how to fix it? or recommend me other browser

---

### Post by Unknown-Demon on 2010-08-12
Alright I see.
Then it must be Pulse Audio.
Go to Terminal again and type:
```
killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo apt-get purge pulseaudio
```In that order.
And then after you do that reboot your computer and test it out.

---

### Post by Unknown-Demon on 2010-08-12
[http://www.google.com/chrome/eula.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-bk&utm_medium=ha&installdataindex=homepagepromo](http://www.google.com/chrome/eula.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-bk&utm_medium=ha&installdataindex=homepagepromo)
If you wish to get another browser go there.
If you want to stick with Firefox tell me the error and I'll try and help.

---

### Post by bender1 on 2010-08-12
it's not an error .i want to enter firefox,it says down starting firefox ,and then nothing happens.

---

### Post by Unknown-Demon on 2010-08-12
If that's the case.
You might want to try and reboot.
and then try and open firefox again.

---

### Post by bender1 on 2010-08-12
i tried a couple of times,no change.

---

### Post by Unknown-Demon on 2010-08-12
Very odd.
Go to terminal and type the following:
```
firefox -safe-mode

```
And if you get a popup asking to reset some stuff check all the boxes and click Continue in safe mode

---

### Post by bender1 on 2010-08-12
(firefox-bin:9498): GLib-WARNING **: g_set_prgname() called multiple times  this is the error i got when i entered that command.

---

### Post by Unknown-Demon on 2010-08-12
From the looks of it it might be a bug.
Did you reinstall Firefox?

---

### Post by bender1 on 2010-08-12
how?

---

### Post by Unknown-Demon on 2010-08-12
Go to terminal and type:
```
sudo apt-get remove firefox
```And then enter your password (Password won't show for security reasons).
and then after its done uninstalling type:
```
sudo apt-get install firefox

```

---

### Post by bender1 on 2010-08-12
tried,not working

---

### Post by Unknown-Demon on 2010-08-12
Should have worked.
My best guess is that it's a bug.
I'd suggest installing chromium 
```
sudo apt-get install chromium-browser
```
And uninstall firefox.
Btw did you ever get your sound working?

---

### Post by bender1 on 2010-08-12
yeah my sound is working now.i installed chrome and i have a little problem.i play evony online.and it uses java,i installed java and when i'm with my mouse over some building it has a delay in desplaying.

---

### Post by Unknown-Demon on 2010-08-12
I'm not a very good java expert lol
I'm happy now that you've got your sound & browser working! :)
I would post a different thread about that so you can maybe get more support for it.

---

