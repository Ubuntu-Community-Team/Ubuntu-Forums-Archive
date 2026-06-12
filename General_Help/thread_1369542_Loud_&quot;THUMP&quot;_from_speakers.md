---
title: "Loud &quot;THUMP&quot; from speakers"
date: 2010-01-01
forum: General Help
---

### Post by HellionDarkLord on 2010-01-01
Some people are getting a loud thump periodiclly from the speakers in Ubuntu 9.10.  (me included.)  Scouring the internet with Google was no help. 

Nice thing about Linux/Ubuntu is that you can get under the hood and fix anything if you know where to look.:guitar:

After scouring the system for sound options I found this:

/etc/modprobe.d/alsa-base.conf
```
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
```

When I saw this I immediately thought about my old guitar amplifier that would "thump" on and off.

Guess what!?!? the sound card is thumping when turning back on after it is idle.  That's a simple fix.

Simply open a terminal and type the following into it 
```
sudo gedit /etc/modprobe.d/alsa-base.conf 
```
Hit enter. Type in your password, hit enter again, and in the text window that pops up change the above lines in the file to this:
```
# Power down HDA controllers after 10 idle seconds
# options snd-hda-intel power_save=10 power_save_controller=N
```

(just add # in front of the word "options", but only on the line that says "power_save=10") 

Save, and reboot the system... No more thumping

YAY!!  

Just thought this might be helpful for audiophiles like myself

HD

---

### Post by cronosh2o on 2010-02-03
Hey HellionDarkLord it works GREAT!
Thanks, it was SO helpful.

---

### Post by HellionDarkLord on 2010-02-06
I was beginning to think nobody else had that problem.  I'm an audiophile and going to school to become a computer engineer, so I just HAD to fix this problem.  Not worth risking my hardware to thumps.  blew the surround off my bass driver. 

Got other posts to post.

Glad to see that this worked for you.

---

### Post by Bachstelze on 2010-02-06
Also watch out for guys with [black hats]("http://xkcd.com/368/"). :D

---

