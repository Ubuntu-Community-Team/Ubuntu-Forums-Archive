---
title: "Wierd Porblem... Sound / Mic help..."
date: 2010-01-23
forum: General Help
---

### Post by Danwhelan on 2010-01-23
**is there any one that knows ACER and ALSA... please....** 			
 			 			 		   		 		 		Running Karmic 9.10

1 - Acer Aspire

2 - The sound was working prior to me playing around... however the mic was not working.... not volume down... not working. 

I followed the following steps 

Download <a href="[ftp://ftp.alsa-project.org/pub/drive...1.0.20.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2")">Alsa drivers v10.0.20

Extracted

Compiled the driver with 
 
./configure
make
sudo make install

Configured alsa-base.conf using sudo gedit - filename 
 Added the following line to the end of /etc/modprobe.d/alsa-base.conf
 
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer

To complete the disaster I rebooted

All this seemed to go off with out a problem.. as in there were no errors that I noticed... however I am from the school of never assume... and I assume that as things are not working that there must have been some sort of error. 

I'm a little worried about un-installing things as the first time I set the system up I have an issue removing some blackberry software and ended up removing the desktop and a whole load of other stuff... 

I've now realised that the version I got wasn't the latest and downloaded the most recent version installed and same. 

Now... sound.... except in Firefox! Firefox sound is there. 

Which makes it even more annoying. 

GNOME sound shows Dummy Output 0.00db - yet sound in FF 

The sound is actually now working.. however only in firefox. 

Various... 

Alsamixer functions well as a program... but like the labour party actually does nothing... there is no control of the sound at all it's either on full volume or off

Alsa conf - again runs through and picks the sound card... sets it up, says OK... then... no sound still dummy output 

Alsa force-reload produces 

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release. (approx 35 times) 

ALSA mixer - key F4... mic is set to capture in red.. so something is working.... but it's not the Mic 

Mic source only gives me the option of front mic.... on the pre 9.10 versions this was a problem for ACER... since no one has answered a acer mic Q for about 8 months I have to assume that this is still the case. 

Arms up in defeat 

Please there has to be one person out there that knows ALSA 

Best and thanks to anyone that might reply

---

### Post by mörgæs on 2010-01-24
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---

### Post by amsterdamharu on 2010-01-24
I found the following helpful on 2 computers using Hardy and no working mic. You might have to re install alsa stuff again since you've changed a lot manually.

> 
    * First you must find which model of sound card you use, so run this command: 

cat /proc/asound/card0/codec#* | grep Codec

It will return model of your sound card(s), for example: "Codec: Realtek ALC260", so your sound card is ALC260.

    * You should open a file in ALSA documentation. This file is here: 

/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz

    * or if that file does not exist, try: 

/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz

(If you compiled your own kernel or ALSA modules, the documentation for your version can probably be found in the source package you used)

    * Search for your model, and take a look at its types, for example I found the following lines for ALC260: 

hp              HP machines
hp-3013         HP machines (3013-variant)
fujitsu         Fujitsu S7020
acer            Acer TravelMate
basic           fixed pin assignment (old default model)
auto            auto-config reading BIOS (default)

Read all of them and try to find the one which is more similar to your sound card, for example if you have a laptop, you can choose "acer".

    * Open /etc/modprobe.d/alsa-base with the following command: 

sudo nano /etc/modprobe.d/alsa-base

    * In Ubunty Jaunty and more recent, the file ends with .conf : 

sudo nano /etc/modprobe.d/alsa-base.conf

Then paste the following line at the end of the file (change MODEL with the type of sound card's model, in our example it should be "acer" (without quotation marks)):

options snd-hda-intel model=MODEL

Double click on the speaker (volume control) edit -> preferences -> tick the capture box and close the window
in volume control you have a tab called recording go there and make sure nothing has a red cross in it.

Forgot to mention that a reboot is needed, sometimes just leave the settings there for 2 days before trying another model.

---

### Post by Danwhelan on 2010-01-25
Thanks for the reply - I have actually already done this.. however I didn't put that in the post so there is no way for you to know that... it's the logical step.. sorry about that/ 

I do get a confusing answer with the chipset as I've Realtek ALC268 on an intel 8280IH... according to the documentation I edit the conf file to reflect an acer.. although I have tried acer and acer-aspire and many other variations. 

I'm convinced that the key to this problem is solving the dummy output issue... 

Anyone 

Many thanks 

Dan

---

### Post by amsterdamharu on 2010-01-25
What's in your ALSA-Configuration.txt.gz file under ALC268?

You've done this and tried all the drivers under ALC268, rebooted (twice sometimes) and checked volume control? When I changed it it didn't work on first reboot but just left it in and later it just seem to work for me (no updates done that could fix it)

* You should open a file in ALSA documentation. This file is here: 

/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz

    * or if that file does not exist, try: 

/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz

(If you compiled your own kernel or ALSA modules, the documentation for your version can probably be found in the source package you used)

    * Search for your model, and take a look at its types, for example I found the following lines for ALC260: 

hp              HP machines
hp-3013         HP machines (3013-variant)
fujitsu         Fujitsu S7020
acer            Acer TravelMate
basic           fixed pin assignment (old default model)
auto            auto-config reading BIOS (default)

---

### Post by Danwhelan on 2010-01-26
Hi there 

Grep codec returns ALC268

In HD config file I have 

quanta-il1    Quanta IL1 mini-notebook
3stack    3-stack model
toshiba    Toshiba A205
acer        Acer laptops 
acer-dmic    Acer laptops with digital-mic
acer-aspire    Acer Aspire One
dell        Dell OEM laptops (Vostro 1200)
zepto        Zepto laptops
test        for testing/debugging purpose, almost all controls can adjusted.  Appearing only when compiled with
$CONFIG_SND_DEBUG=y
auto        auto-config reading BIOS (default)

I'll try all of them and let you know... 

However the other issue is that because of the "dummy output" 

Double click on the speaker (volume control) edit -> preferences -> tick the capture box and close the window in volume control you have a tab called recording go there and make sure nothing has a red cross in it. 			 		

I can't do this as all options are blank and greyed out... 

Example.. sound preferences tab

hardware tab = blank 
Input tab = blank
Output = dummy output stereo (only option) 
Applications = no applications are playing audion (blank) 

Alsa mixer output - sorry if it's not straight... but as you can see for example mic boost can be muted.. but mic shows no control from on to mute... note I have turned these all up to full and done the same with F4

  &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;      &#9474;
&#9474;     &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;      &#9474;
&#9474;     &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;      &#9474;
&#9474;     &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;      &#9474;
&#9474;     &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;      &#9474;
&#9474;     &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;      &#9474;
&#9474;     &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;      &#9474;  &#9474;      &#9474;
&#9474;     &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9500;&#9472;&#9472;&#9508;       &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;       &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;       &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;      &#9474;
&#9474;     &#9474;OO&#9474;       &#9474;MM&#9474;                                      &#9474;OO&#9474;      &#9474;OO&#9474;      &#9474;
&#9474;     &#9492;&#9472;&#9472;&#9496;       &#9492;&#9472;&#9472;&#9496;                                      &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;      &#9474;
&#9474;      31       38<>41    40<>40     50<>50    50<>50     42<>42    11<>11     &#9474;
&#9474;  < Master >  Headphon    PCM      Front Mi  Mic Boos     Beep    Speaker    


Amixer outputs 

smoo@Danny:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 20 [31%] [-44.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 24 [38%] [-40.00dB] [off]
  Front Right: Playback 26 [41%] [-38.00dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 102 [40%] [-30.60dB]
  Front Right: Playback 102 [40%] [-30.60dB]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 2
  Front Left: 1 [50%]
  Front Right: 1 [50%]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 2
  Front Left: 1 [50%]
  Front Right: 1 [50%]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 13 [42%] [3.00dB] [on]
  Front Right: Capture 13 [42%] [3.00dB] [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 12
  Mono:
  Front Left: Playback 5 [42%] [-14.00dB] [on]
  Front Right: Playback 5 [42%] [-14.00dB] [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 42 [35%] [-9.00dB]
  Front Right: Capture 42 [35%] [-9.00dB]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 7 [11%] [-57.00dB] [on]
  Front Right: Playback 7 [11%] [-57.00dB] [on]

I hope there is something in here that might give you a clue... I guess if nothing was working it would be less annoying.. 

It's a great pity... because I love this OS... but it seems to have been totally let down here by just the sound 

Thanks so much for helping 

Dan

---

### Post by amsterdamharu on 2010-01-26
You can make sure alsa is used, right click volume applet and choose preferences here choose your alsa thing.

See if restarting alsa-server gives any errors:

```
sudo /etc/init.d/alsa-utils restart
```

---

### Post by Danwhelan on 2010-01-26
Hi there

preferences in the gnome sound app are blank... there are no choices other than dummy output... 

Alsa restart produces... 


danny@Danny:~$ sudo /etc/init.d/alsa-utils restart
 * Shutting down ALSA...                                                 [ OK ] 
 * Setting up ALSA...                                                    [ OK ] 

Still no sound :-(

---

### Post by Danwhelan on 2010-01-26
Also 

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Danwhelan on 2010-01-26
Small update... 

I now get sound at start up... as in after password input 

Then nothing... 

Dan

---

### Post by amsterdamharu on 2010-01-26
Ok dummy passes the sound to dev/null
[http://alsa.opensrc.org/index.php/Dummy](http://alsa.opensrc.org/index.php/Dummy)

The dummy is activated after reboot, maybe get rid of the following file and reboot to see if alsa is re initialized but I fear you might have to uninstall and install alsa (use synaptec)

sudo mv /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-notwork

---

### Post by Danwhelan on 2010-01-26
Can you just tell me how to remove and replace ALSA... I'm just worried that it's going to remove 50 other components that I need. 

Also will it totally remove and replace? When I reinstalled ALSA the first time the edited parts of the alsa-base.conf file were still there? 

Thanks 

Dan

---

### Post by Danwhelan on 2010-01-26
[LEFT]I've just realised after rereading this a few hours later in my head.

"But remember! It's a really dummy soundcard. Sound being played over one of the playback channels can not be recorded trough the record channels again. The sound is really sent to /dev/null."

The problem is Dummy output.... 

I hear sound.... sometimes... 

[/LEFT]

---

### Post by Danwhelan on 2010-01-27
Further update... sound works in Firefox... however gnome sound controls have no effect on the volume level... 

Interesting? Would there be a way to find out the firefox sound settings and copy them in to alsa? 

Dan

---

### Post by Danwhelan on 2010-01-27
speaker-test -Dplughw:0,0 -c2

Working!!! Would you believe it... it works here.. no where else though. 

Danny:~$ amixer |grep Mic
Simple mixer control 'Mic Boost',0
Items: 'Mic' 'Internal Mic' 'Line'
Item0: 'Mic'
Simple mixer control 'Internal Mic Boost',0

Mic is dead... 

However if I run alsamixer from the console... then F4

I get 

   <Line In >   Mic Boos    Capture     Digital     Input So    Internal 

Now input so was not there before.... and if I navigate to it I get three options above it. 

Mic internal and line... but no level indicator... just the text. 

Any ideas anyone???

---

### Post by perspectoff on 2010-11-14
> * First you must find which model of sound card you use, so run this command:

cat /proc/asound/card0/codec#* | grep Codec

It will return model of your sound card(s), for example: "Codec: Realtek ALC260", so your sound card is ALC260.

* You should open a file in ALSA documentation. This file is here:

/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz

* or if that file does not exist, try:

/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz

(If you compiled your own kernel or ALSA modules, the documentation for your version can probably be found in the source package you used)

* Search for your model, and take a look at its types, for example I found the following lines for ALC260:

hp HP machines
hp-3013 HP machines (3013-variant)
fujitsu Fujitsu S7020
acer Acer TravelMate
basic fixed pin assignment (old default model)
auto auto-config reading BIOS (default)

Read all of them and try to find the one which is more similar to your sound card, for example if you have a laptop, you can choose "acer".

* Open /etc/modprobe.d/alsa-base with the following command:

sudo nano /etc/modprobe.d/alsa-base

* In Ubunty Jaunty and more recent, the file ends with .conf :

sudo nano /etc/modprobe.d/alsa-base.conf

Then paste the following line at the end of the file (change MODEL with the type of sound card's model, in our example it should be "acer" (without quotation marks)):

options snd-hda-intel model=MODEL

Double click on the speaker (volume control) edit -> preferences -> tick the capture box and close the window
in volume control you have a tab called recording go there and make sure nothing has a red cross in it. 

That advice does nothing for me.

---

