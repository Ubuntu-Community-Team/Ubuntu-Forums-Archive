---
title: "Sound problem in headphones in 10.04"
date: 2010-05-09
forum: General Help
---

### Post by roshanjose on 2010-05-09
i installed 10.04 on my desktop system and i am not getting sounds on my headphones...but i can hear from my speakers...previously i had 9.04 and everything was fine...can anyone help me..

---

### Post by JakeLawrence on 2010-05-10
I have the exact same problem! I'm doing research on it right now. I'll update you if I find anything. It might help if you post the make/model of your PC and the output of this code in the Terminal (Applications->Accessories->Terminal):

```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```

I don't know how new to Ubuntu you are, but if you're having problems entering your password with the Terminal (like I was a couple of weeks ago), go ahead and enter the password where the blinking bar is (there's no visual feedback) and press enter.

---

### Post by MadZe on 2010-05-12
Hello guys; I had the very same problem, and I found a way to solve it, at least with this sound card: 

```

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```

I added these 3 lines at the end of the /etc/modprobe.d/alsa-base.conf file; Give it a try! Just enter in a terminal:

```

sudo vi /etc/modprobe.d/alsa-base.conf

```

And add these lines at the end of the file:
```

options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

```

Then reboot, and it may work!
Enjoy!
MadZe

---

### Post by stinkeye on 2010-05-12
Installing gnome-alsamixer fixed this for me.
See this post [**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=9280229&postcount=6[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=9280229&postcount=6")

---

### Post by roshanjose on 2010-05-12
Here's the output:

roshan@roshan:~$ uname -a
Linux roshan 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

roshan@roshan:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

roshan@roshan:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

roshan@roshan:~$ head -n 1 /proc/asound/card*/codec#*
Codec: SigmaTel STAC9221 A1
roshan@roshan:~$

---

### Post by lidex on 2010-05-12
What is the make/model of this PC?

---

### Post by roshanjose on 2010-05-12
MadZe it worked according to what you said.....thank you very much

thank you everyone for helping me.....

---

### Post by roshanjose on 2010-05-12
in what way should i say that....is there any command so that I can say the exact moke/model of my PC...

i guess there's some package that gives the entire info about the PC...but i dont remember the package name..

---

### Post by lidex on 2010-05-13
I wouldn't worry about it if it works now.

---

### Post by Alonso_91 on 2010-05-13
Stinkeye is right... gnome-alsamixer fixed the problem for me too! Thanks for the info :D

---

