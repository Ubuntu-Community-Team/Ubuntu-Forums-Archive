---
title: "Ubuntu and Skype going forward"
date: 2009-11-11
forum: General Help
---

### Post by jf1991999 on 2009-11-11
I have been a Ubuntu user since 7.04 and have put up with a buggy version of skype by learning how to get around its issues.  Skype recently released a new version (2.1 beta) that fixed all the outstanding bugs, however it exclusively used Pulse Audio which totally bombed my system.

I did a fresh install of Karmic hoping that the new skype would work and found that unfortunately it was still unusable.  My Laptop is an HP Pavilion dv6000 which is a standard laptop used by large numbers of people.  Skype is a critical application for me and many others and having it work 100% out of the box is extremely important.

I was able to get skype working after many hours of research and trial and error by completely removing Pulse and installing esound.  While this fixes skype it screws up the default sound GUI provided by Ubuntu.  I added the GNOME ALSA GUI but it is not very clean.

My reason for this post is to ask that effort be put into ensuring that Skype is fully supported out of the box in future Ubuntu releases.  I was close to having to abandon Ubuntu for Windows (something that would greatly pain me!) because of the issues with Skype.  Karmic was flawless in all other areas.  It has matured enormously over the last 2 years and is on the verge of becoming accessible to a wide audience.  100% support for applications like Skype is critical if it is to progress.

---

### Post by kostkon on 2009-11-11
What exactly was your problem with Skype and PulseAudio? Why are you saying that it was unusable?

---

### Post by markbuntu on 2009-11-11
FYI The skype devs have been working with the pulseaudio devs and have fixed all oustanding issues between skype and pulseaudio which have been incorporated into the latest skype release which is fully compatible with the pulseaudio used in karmic.

Wether that version made it into karmic, I do not know.  I don't use skype. 

Also, the ubuntu packagers make a number of changes to pulseaudio that seem to be detrimental to many people's pulseaudio experience in ubuntu, like removing important modules and rewriting the udev rules. We can only hope that they stop doing that.

If you want to get their attention file a bug report against pulseaudio at launchpad.

---

