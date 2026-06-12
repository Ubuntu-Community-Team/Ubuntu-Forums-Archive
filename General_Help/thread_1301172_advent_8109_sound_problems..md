---
title: "advent 8109 sound problems."
date: 2009-10-25
forum: General Help
---

### Post by teh'p3nsi0n3r on 2009-10-25
Hi I am currently sitting here trying to fix my friends laptop.
His XP install died for unknown reasons but after seeing my ubuntu install in action has decided he wanted to give ubuntu a bash. :)
So far is impressed with it working on his laptop.

laptop specs in the link below, it is an advent 8108.

[http://www.uktsupport.co.uk/advent/laptop/8109.htm](http://www.uktsupport.co.uk/advent/laptop/8109.htm)

Everything is working great minus sound. 
Volume switch is showing in the top right hand corner of the screen but showing no devices when going into the volumes properties.

I had a browse around the forums and had a look at the following link.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Now after running.

aplay -l

this shows a very similar result as:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


after this ran the last command on the bottom of the tutorial which was.

sudo alsa force-reload

This resulted in the sound working, and checking the sound card settings in the top right hand corner showed the device for the sound card in there. But after restarting ubuntu there was no sound again. But repeating these steps would then result in us getting sound.
How can we save the config so the sound stays after rebooting.

thanks.

---

### Post by teh'p3nsi0n3r on 2009-10-25
sorry to be impatient. 
anyone?

thanks.

---

### Post by teh'p3nsi0n3r on 2009-10-25
no worries fixed. had installed a driver for on board modem earlier from restricted drivers and this seems to messed up alsa. now uninstalled. now fixed. :)

---

