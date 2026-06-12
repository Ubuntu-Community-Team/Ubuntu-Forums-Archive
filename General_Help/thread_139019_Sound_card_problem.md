---
title: "Sound card problem"
date: 2006-03-03
forum: General Help
---

### Post by Sonya Williams on 2006-03-03
Ok, this is probably a noob question, as I am relatively new to Ubuntu...

So, I have a Dell Dimension 8400 on which I have recently installed ubuntu. All of my other hardware works perfectly (printer, scanner, the works :)), but I can't seem to get my sound to work (admittedly, I haven't tried much, but that's only because I don't know what to try!):-k . I have an integrated Creative Sound Blaster Audigy sound card, and the problem is definately not with my speakers as the work fine on my (Windows) laptop. You can find the full specs [here.]("http://reviews.cnet.com/Dell_Dimension_8400/4507-3118_7-30919189.html")

Please excuse my "noob-ness". ;)

---

### Post by hw-tph on 2006-03-03
Type **sudo lspci | grep audio** to see what kind of audio hardware you have.


Håkan

---

### Post by Phixion on 2006-03-03
Hi, sorry to hijack this thread but I'm having the same issues (i think). I typed what you suggested and got this:

0000:01:0d.0 Multimedia audio controller: Creative Labs SB Audigy LS

I'm pretty sure I have a soundblaster live 24bit... What do I need to do to get my sound working? Thanks.

---

### Post by akiro.yamamoto on 2006-03-03
A slight modification:
sudo lspci -v | grep audio
That will give you the chipset of the card, which helps identify which driver you have to use. Note the " -v " switch, very important. ;)
when you have identified the chipset go here: 
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs) 
Look for your card and chipset, click on the link in the chipset column for futher 
instructions..

---

### Post by akiro.yamamoto on 2006-03-03
I also found this link detailing some problems others had with this card and possible solutions.
[http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=1195&forum=5](http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=1195&forum=5)
Hope this helps. ;)

---

### Post by hw-tph on 2006-03-03
The Audigy LS, or Dell Audigy, isn't a "real" Audigy - it doesn't use the emu10k series DSP chips like the SB Live and other Audigy cards, but rather the rather obscure CA0106. There is an Alsa driver for it, snd-ca0106, that comes with the stock Ubuntu kernels.

I have not used this card in person so I don't really know what actions it may require. You may want to start out by trying **lsmod | grep snd** to see what sound modules are loaded and if the snd-ca0106 module is there.


Håkan

---

### Post by Sonya Williams on 2006-03-04
Thanks for your help everyone, I really appreciate it, but it seems that I already have the driver installed :???: 
Anyone know what could be causing this now?

EDIT: Ok, I tried reinstalling the driver and I keep getting this error:
[I]
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).[/I]

---

### Post by akiro.yamamoto on 2006-03-04
Install build-essential and linux-headers.

---

### Post by Phixion on 2006-03-07
SORTED! Thanks all.

Heres what I did...

run alsamixer in terminal and turn up the volume for "analog c, f, r, s" and it should work ;)

---

### Post by SolarBear on 2006-03-12
Huh... I may sound dense here (and I may be, heh ;) ) but I have the exact same problem as you, Phixion - trying to use my CL Audigy LS - and my snd_ca0106 driver is loaded but alsamixer won't show anything related to "analog c,f,r,s". Care to give me more details ? Perhaps it's a command I have to input ?

Thanks for the help.

---

### Post by xshady87 on 2006-03-19
I tried what you said, and my sound works now, but the sound is extremely raspy. Any suggestions?

---

### Post by learning curve on 2006-03-19
Go to System/preferences/sound and make sure that your sound card is in the drop down box.  Then Double click on your speaker in the upper right of your screen and your alsa mixer will pop up and make sure your volume levels are up.  
You can also go to creative.com and look for the linux driver for that model sound card, they may have it there.

Hope this helps.  Learning Curve:D 

"If you strike me down, I shall become more powerful than you can possibly imagine."  Obewan loves Ubuntu!

---

### Post by xshady87 on 2006-03-20
I tried that, everything seems fine, but the sound is distorted (almost as if the bass and treble were really high.)

---

