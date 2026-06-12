---
title: "Pulseaudio was working, now it isn't."
date: 2009-10-12
forum: General Help
---

### Post by Vince N on 2009-10-12
Hey all

Running an Acer Aspire 5315 on Jaunty.  For some reason today my pulseaudio quit working.  It plays but all I hear out of it is static when it plays a noise.

I have not installed anything or done any changes recently that I can think of that might have caused this.  I had to restart the computer earlier today and that was all

Does anyone have ANY idea what might be going on?  Windows on this laptop is dog slow for doing what I do with sound.

---

### Post by zeronothing on 2009-10-12
to try and recover pulseaudio try this:

1.) first close the app that has stopped playing sound.

2.) open up terminal and do this command "sudo alsa force-reload"

3.) reopen the app and see if sound is now playing. 


This process helped me with a similar problem your having.

---

### Post by Vince N on 2009-10-13
You sir are a God

Ok maybe not a god but you made me very happy.  Force reload of Alsa did the trick.

This has me wondering though first of all do you have any idea what may have caused this in the first place?  I'm annoyed that I know of no obvious cause and thus don't know how to fix the issue or avoid breaking it again in the future.  What does forcing Alsa to reload do that restarting the computer does not that caused it to work now when restarting the PC or doing a straight shut down and then reboot didn't?

I guess I should just be happy given the horror stories I've heard about PulseAudio but to be honest other than weird hickups and glitches like this it's behaved rather well for me.

---

### Post by Vince N on 2009-10-14
Bumping Thread for great justice because I'm still having this issue periodicity.  Reloading Alsa is temporary resolving it but every few hours or so my speakers start spewing static again and I'm back where I started.

It would be nice if I could figure this out before Karmic comes out later this month.

---

### Post by zeronothing on 2009-10-14
certain programs cause this issue for me more frequent than others. One program in particular is "Skype." I have had major issue with skype and it causing my sound to go out. Rhythmbox it happens to every now an again. Also the more apps you have using pulsaudio, there is a great chance of sound failing. This is just in my experience. Right now I have been using 9.10 and I don't seem to be having the issue anymore with pulseaudio.

---

