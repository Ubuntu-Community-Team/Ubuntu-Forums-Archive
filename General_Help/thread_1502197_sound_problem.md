---
title: "sound problem"
date: 2010-06-05
forum: General Help
---

### Post by portia on 2010-06-05
Hi all,
I do apologise if that's not the right forum for Ubuntu 10.10 alpha. I couldn't find the alpha section here.

I decided to give U10.10 a try.  I'm not new to linux and know what running an alpha version of a distro means:)

Basically, the sound is not working. I guess it's something simple to do with PulseAudio or system settings.

My card is audiophile2496 - the right modules are loaded (snd_ice1712)
I checked alsamixer and the channels are not muted. There're no errors when I play a film or some music, just nothing comes out of the speakers. The Pulseaudio Volume meter's levels indicate that something IS being played. There are no system sounds either (I'm not sure if ubuntu gives any system sound on the startup at all)

I can't find the Sound section in System>Administration or System>Preferences. I don't know if it's relevant but I installed Gnome Shell (Actually, I don't know if it's running right now.)

Might I be missing some packages?

Thank you for reading it.

---

### Post by Barafu Albino Cheetah on 2010-06-05
Install pavucontrol. Use it to see if pulseaudio sees your soundcard and it is not muted (a separate button for mute, not a volume scrollbar). Report here.

---

### Post by portia on 2010-06-05
Thanks for your reply.
It's already been installed. I ran it and everything seems to be fine - It's not muted. The level indicates active sound streams, but still nothing comes up from the speakers. There's nothing wrong with the speakers. When I reboot to Slackware on this computer, the sound is fine.

---

### Post by dino99 on 2010-06-05
first goto : system pref sound to see if your sound hardware is identified

then install paprefs and gnome-alsamixer (set your prefs with it)

note: 101.10 can be found into "developpement & programming" forum

---

### Post by portia on 2010-06-05
> **dino99 said:**
> first goto : system pref sound to see if your sound hardware is identified

then install paprefs and gnome-alsamixer (set your prefs with it)

note: 101.10 can be found into "developpement & programming" forum

As I mentioned above, Sys=>Pref=>sound is missing. It seems that I'm not the only one with this problem. I right-clicked on the menu and tried to edit it but there was no 'sound' option unchecked.

Additionally, if I click on the volume icon in the top right-hand side corner of the screen, there's an option 'sound preference'. When I click on it, nothing happens (nothing opens)

---

### Post by portia on 2010-06-05
I installed Ubuntu Studio 9.04 (amd64) - and have got exactly the same problem -  I mean the System==>preferences==>sound exists and looks okay, but still no sound whatsoever.

Any hints

---

### Post by portia on 2010-06-05
FYI
I knew it was something to do with pulseaudio/. This is the solution:
[http://www.feeditout.com/2010/05/08/ubuntu-10-4-pulseaudio-m-audio-audiophile-2496/](http://www.feeditout.com/2010/05/08/ubuntu-10-4-pulseaudio-m-audio-audiophile-2496/)

---

