---
title: "problems getting dvi output to work on Jaunty"
date: 2009-10-12
forum: General Help
---

### Post by graza on 2009-10-12
Hi all

Ok I have a Nvidia9200 card that was working fine with a BenQ e2200hd monitor (VGA to VGA connection). I moved the computer of the desk and this meant I needed to use a VGA extension cable. Problem! the EDID is no longer transmitted so ubuntu doesn't know which resolutions the monitor supports, so it defaults to 1024x768 (there are no higher options in the Nvidia X settings)

I know, I'll get a DVI to HDMI cable, its digital, a longer cable should work fine... Now, with both cables plugged in, in NVidia X setings I can see CRT0 (VGA) and a second screen (DVI, correctly recognised as the BenQ monitor). However if I switch them round I can't get anything displayed via the DVI-HDMI output.  I've tried setting the VGA and DVI screens as separate X screens (thinking I could boot in the VGA low resolution then switch over to the correct resolution via DVI), the VGA output works but I get nothing when switching to the second X screen (Ctrl+alt+Function key eight). 

I hope this makes sense... All I want is to get the correct resolution working, whether by VGA or DVI doesn't matter at this stage (obviously DVI should give better quality but this is my work computer and I just need to get on with work...) 

Thanks all you Ubuntu developers and helpers - great work. But now I need a little help to resolve this.

Graza

---

### Post by graza on 2009-10-19
Hi
no reply yet...  

Let me shorten my original post:

1) how can I force the video card VGA Dsub resolution to 1920x1080

or

2) how do I troubleshoot the DVI output

Help!

---

### Post by graza on 2009-10-23
Bump

Starting to get crossed eyes now from the upscaling of the low resolution. :(

---

### Post by P4man on 2009-10-23
ive seen several posts of problems with DVI and nvidia and missing EDID. I can only say it works for me, but clearly you're not alone.

Perhaps you can try grandr? Its in the repo's. Or you could try updating your nvidia drivers and hope that solves it. Which one do you have now ?

edit: also have a look here:
[https://answers.launchpad.net/ubuntu/+source/xorg-server/+question/39299](https://answers.launchpad.net/ubuntu/+source/xorg-server/+question/39299)

Its a long read, but could be worth it.

---

### Post by graza on 2009-10-27
OK, first of all thanks to everyone that's read the posts and P4man in particular for his helpful advise.

I fiddled for a bit longer, and eventually discovered that the monitor's auto switch to HDMI option was set to the default of 'off', explaining why I couldn't get a picture (although the monitor's information was still being sent back to the computer via the HDMI, so you could see it in NVIDIA-SETTINGS OK...  this through me off the scent for a while).

Anyway, I have left the Dsub VGA and the DVI-HDMI cables attached to the monitor. I've also disabled the VGA monitor in NVIDIA-SETTINGS (since it is low resolution) and made the DVI input the only active X screen. When the computer goes through BIOS and kernel selection the picture is sent by VGA, halfway through I guess X starts, switches to DVI output and now (with auto swich to HDMI set to 'on' the monitor now goes to 1920x1080 resolution being fed by the new cable (incidentally its from 7dayshop (UK) - cheap but good quality and works just fine if anyone needs a cable, DVI is digital so why buy a really expensive one?)

So, problem solved, my faith in Ubuntu restored, my eyes are recovering.:D Thanks everyone!

Graza

---

