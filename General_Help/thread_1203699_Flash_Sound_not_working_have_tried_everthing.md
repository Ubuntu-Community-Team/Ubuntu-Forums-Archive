---
title: "Flash Sound not working have tried everthing"
date: 2009-07-03
forum: General Help
---

### Post by acidpiper on 2009-07-03
Please Help - i am fairly new to ubuntu but not completely incompetent ( i hope not)

FLASH PLAYER WILL NOT PLAY SOUND  i have done the following to try and repair this:

Uninstalled and reinstalled flash player (via terminal and synaptic Manager)

Uninstalled and reinstalled FireFox

Uninstalled and reinstalled ubuntu 9.04

and i have used the following commands:

sudo aptitude install alsa-oss
gksudo gedit /etc/firefox/firefoxrc (the window was empty)
sudo apt-get install libflash support (Couldn't find package libflash)

I was starting to wonder whether it could have somthing to do with my sound card (ATI 4670 HDMI)but I do have sound when i play mp3's etc so i am stumped PLEASE HELP

---

### Post by moster on 2009-07-03
buddy, I have no I idea what you really want with that...

All I do when fresh install ubuntu is install "ubuntu restricted extras" from add/remove menu and that is all. Flash, mp3 codecs... all is working like it should.

edit:
correction. beside that I install gstreamer extra plugins. That is installed from add/remove menu, not apt-get or synaptic.. It simply must work all, if you havent got some hardware incompatibilities.

---

### Post by acidpiper on 2009-07-03
Thanks - i checked and i have installed all the gstreamer codecs

---

### Post by moster on 2009-07-03
hm... you little confuse me with this, I just do not know why you doing this. Someone told you or you just know that?

```
sudo aptitude install alsa-oss
gksudo gedit /etc/firefox/firefoxrc (the window was empty)
sudo apt-get install libflash support (Couldn't find package libflash)
```

I can tell you exactly how it should be done for majority.

1. Install ubuntu
2. Update it.
3. Install radeon drivers from menu system > administrations > hardware drivers.
4. Install ubuntu restricted extras. At this point, you should have fully working flash in firefox and basic codecs.
4. Optional. Microsoft core fonts, everything related to gstreamer and some mplayer.

If any of this help you, I am happy, if not sorry :)

---

### Post by acidpiper on 2009-07-03
The commands i got from research in ubuntu forums and google

---

### Post by acidpiper on 2009-07-04
Bump please help

---

### Post by kostkon on 2009-07-04
Open a terminal and give
```
aplay -l
```
and post the output here to see if you have more that one audio devices and Flash sends its sound to the one that you don't use.

---

### Post by acidpiper on 2009-07-05
i do have more than one but i switched the motherboard one off- (you have replied to another thread i posted re pulseaudio)

---

### Post by Brian R. on 2009-07-06
I had the same problem and this is how i solved it.
Go to [http://get.adobe.com/flashplayer](http://get.adobe.com/flashplayer) and get Flash Player 10.022
Click the combo box button and select .deb for ubuntu 8.04+
Click the download button and save the file to your desktop.
Then install the deb file. Next in firefox go to your add-ons plugins and if you have an earlier version of shockwave flash click disable. This worked for me.

Brian R.

---

### Post by gasto on 2009-07-06
> **Brian R. said:**
> I had the same problem and this is how i solved it.
Go to [http://get.adobe.com/flashplayer](http://get.adobe.com/flashplayer) and get Flash Player 10.022
Click the combo box button and select .deb for ubuntu 8.04+
Click the download button and save the file to your desktop.
Then install the deb file. Next in firefox go to your add-ons plugins and if you have an earlier version of shockwave flash click disable. This worked for me.

Brian R.

How do I get version 10.022 , that doesn't sound like an actual version. Did you mean 10.0.22 ?

The most recent version is 10.0.22.87 , are you referring to that one?

Also my audio system specs:

/etc/apt$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Lambda [Lexicon Lambda], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by gasto on 2009-07-06
> **Brian R. said:**
> I had the same problem and this is how i solved it.
Go to [http://get.adobe.com/flashplayer](http://get.adobe.com/flashplayer) and get Flash Player 10.022
Click the combo box button and select .deb for ubuntu 8.04+
Click the download button and save the file to your desktop.
Then install the deb file. Next in firefox go to your add-ons plugins and if you have an earlier version of shockwave flash click disable. This worked for me.

Brian R.

I did what you suggested with Flash version 10.0.22.87 and audio did not work.

---

