---
title: "PulseAudio Removal and Recompiling"
date: 2012-07-16
forum: General Help
---

### Post by nankura on 2012-07-16
Hey guys

basically. i want to remove alsa, pulse, and sound drivers from ubuntu without removing the entire desktop, and then install and recompile the newest versions of both pulse and alsa. with tools etc so that i still have the volume bars booting up for pulse

And im wondering how id go about making this happen

---

### Post by dino99 on 2012-07-16
try: 

Here is a method to remove Pulse Audio and return Alsa the default configuration!

PulseAudio is removed already:

    sudo apt-get remove pulseaudio

    sudo apt-get install esound

Then make a backup file and it deletes 70pulseaudio

    sudo cp / etc/X11/Xsession.d/70pulseaudio / etc/X11/Xsession.d/70pulseaudio.back

    sudo rm / etc/X11/Xsession.d/70pulseaudio

And finally, we will "explain" that Gnome does not use PulseAudio but Alsa ... We must therefore go to the menu

    System -> Preferences -> Sound

And repositioning in "Audio Conference", the sound capture to "ALSA"

Then head in

    System -> Preferences -> Startup Applications

And deselect the "PulseAudio Session Management"

And finally, a little housekeeping of your personal files ... Go to your home directory and backup / deletion of files asoundrc so that all this is reconfigured with ALSA:

    cd ~

    cp. asound * filename

    rm. asound *

[https://wiki.ubuntu.com/PulseAudio/](https://wiki.ubuntu.com/PulseAudio/)
[https://launchpad.net/~diwic/+archive/pulseaudio-testing](https://launchpad.net/~diwic/+archive/pulseaudio-testing)

---

