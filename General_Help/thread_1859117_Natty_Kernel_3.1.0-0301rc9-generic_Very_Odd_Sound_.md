---
title: "Natty Kernel 3.1.0-0301rc9-generic Very Odd Sound Issue"
date: 2011-10-13
forum: General Help
---

### Post by dwlima on 2011-10-13
I /etc/modprobe.d I blacklisted "snd_hda_intel" so that only my "Bose USB Audio - Analog Surround 4.1 Output" shows under Sound Hardware. Since it was not at default 0, my system would default to the onboard sound card. 

The sound would then be muted and unmuting did not help. So, I [COLOR=#555555][FONT=Arial]navigated to */system/gstreamer/0.10/default* and changed the "audiosink" and "musicaudiosink" to"osssink".

Now, the strange part is that in order for me to get sound, I need to CHANGE the output volume. The moment I change it, the sound comes on and I can move the volume bar anywhere I want and everything is fine. It is not muted. It "looks" fine, but I need to move that output volume bar a little to get the sound to come on. 

Any ideas would be appreciated.
DWLima
[/FONT][/COLOR]

---

