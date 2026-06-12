---
title: "No sound, strange...."
date: 2009-06-25
forum: General Help
---

### Post by SatieB on 2009-06-25
Hi,
I'm usinga HP DV6 laptop (Kubuntu). Sound gave no problem with kernel 2.6.28.11. After going to 2.6.28.13 sound disappeared. If I return to .11 kernel the sound is back again. What has changed between these kernels/
Any help is appreciated.

---

### Post by Megrimn on 2009-06-25
My advice may not have anything to do with your kernel specs, but I would check and make sure all your sound drivers are set to ALSA.  

that's in System Settings > Sound System > click on the Hardware tab.

In there the audio device is called "Advanced Linux Sound Architecture" (other wise known as ALSA)

---

### Post by SatieB on 2009-06-26
Thanks for the advice. I'm using Kubuntu and when I look at system settings I cannot find any hardware tab. I see something like "multimedia" which gives me information on the hardware installed, some testing button and a tab called "backend" whith some Xine info.
Any other suggestions?

---

### Post by Chris Musampa on 2009-06-26
System Settings > Multimedia, click Audio Output in the left pane then click on each of the devices in the list on the right pane and click Test, when you find a device that works move it to the top of the list.

---

### Post by SatieB on 2009-06-28
I did what you suggested but to no avail. Both HDA Intel STAC92xx analog and the Pulseaudio. do not produce any sound. When testing pulseaudio, Phonon kicks in and and report that pulseaudio does not work and that it will fall back op HDA Intel. As Kubuntu does not use pulseaudio, I'm not surprised that it won't work.
As I reported earlier, within the .11 kernel sound is working correctly. So what went wrong with the .13 kernel?

---

### Post by SatieB on 2009-06-30
This one is solved!
Following this link: [http://kubuntuforums.net/forums/index.php?action=printpage;topic=3104351.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3104351.0)

See for the solution the the last entry in that thread.

The solution installs the newest alsa drivers through a script which can be found here: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

---

