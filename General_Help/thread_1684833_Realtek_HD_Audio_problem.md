---
title: "Realtek HD Audio problem"
date: 2011-02-09
forum: General Help
---

### Post by zeitxgeist on 2011-02-09
Hi people,
 
Completely new to Ubuntu and Linux in general, so forgive me if I came across a complete newbie. :P
 
I recently installed Ubuntu using Wubi and everything seems to be going great - except for one small problem. My audio doesn't quite sound right. My laptop has four inbuilt satellite-y speakers and a 1.5" subwoofer (overkill I know, but I love it), and can only get sound through two of the satellites now, which results in the sound being fair quieter than what it was, and no where near as good.
 
I've tried google searching and can't seem to find a solution or anyone with the same problem. Checking devices produces no results for my Realtek HD Audio and can't find a driver or something similar to make it actually work properly. Booting up Windows it works fine.
 
I'm not at home right now as I'm working (clearly), so I can't post with any real information right now, but some tips would be helpful.
 
It's running Ubuntu 10.10.
 
Thanks. :)

---

### Post by DrReaper on 2011-02-09
Check out the Realtek website and see if there are any linux drivers for your laptops sound system. I would also check with the manufacturer of the laptop for linux drivers.

---

### Post by lidex on 2011-02-09
Can you provide more system info please? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by zeitxgeist on 2011-02-09
I attempted to run that, however I get an error
invalid option --'0'.

If I remove the -0, I get a bunch of attempts to connect to that address, so, not sure if I'm doing it right or not, but I coped it exactly how you typed it out. :)

I also downloaded the codec from the Realtek site as well and attempted following the instructions for installation, but encounter an error trying to decompress it. 

Running tar xfvj alsa-driver-1.0.xx.tar.bz2 results in an error (yes I'm putting in the correct file path :P)... "Cannot open, no such file or directory exists," though when I type only tar xfvj I get another error of sorts saying that f is an old option and requires an argument, if that's relevant. That's the command the installation readme tells me to do.

---

### Post by zeitxgeist on 2011-02-10
Ah, it gets worse. I finally managed to figure out how to install it mostly on my own :D.

Problem is, now I have *no* sound at all. Any help would be appreciated. :(

---

### Post by lidex on 2011-02-10
OK. That is a diagnostic script that collects system info. Just **copy-and-paste** into a terminal and at the prompt select the upload option. Post the link to that info in your next post.

---

### Post by zeitxgeist on 2011-02-10
Ah, there we go.


[http://www.alsa-project.org/db/?f=8c8006e4642f819c54a5c6f34830216aa236c0b2](http://www.alsa-project.org/db/?f=8c8006e4642f819c54a5c6f34830216aa236c0b2)

---

### Post by mastablasta on 2011-02-10
did you try:
 
[FONT=Courier New]sudo alsaconf[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]To configure the card?[/FONT]

---

### Post by zeitxgeist on 2011-02-11
Whenever I try to use alsaconf I just get command not found. :(

Also, just running the system test tool, and I get this for audio:

Detecting your sound device(s):

cat: /proc/asound/cards: No such file or directory

Is this correct?

I'm assuming this is relevant.

---

### Post by zeitxgeist on 2011-02-12
Solved! :D

Restored my sound to how it was by removing the updated codec which restored sound to two of the four speakers,

then did this:

```
sudo nano /etc/modprobe.d/alsa-base.conf
```

And added

```
options snd-hda-intel model=lenovo-ms7195-dig
```

At the end of the file (using Lenovo Y510) - all four speakers and subwoofer now work!

---

