---
title: "Help Building a Quick Shell Script"
date: 2010-03-04
forum: General Help
---

### Post by ngrieb on 2010-03-04
I was hoping that someone could help me with a very simple shell script that creates a PC speaker beep when a certain background process or script stops, and possibly reports the run time of that process.
Thanks in advance.

---

### Post by lavinog on 2010-03-05
does the beep command work for you?
(It doesn't on my current system, but has in the past for older systems)

---

### Post by jmichelsen on 2010-03-05
ok, there are a few ways to do this but first, you need to make sure beep is installed. It currently isnt installed by default (dunno why that changed)

```
sudo apt-get install beep
```

after thats installed, all you really need to do is add beep to the end of your scrip to it will beep when it's done. Beep is pretty versitile so you can actually have it do different pitches for diff scripts or whatever, but you can read the man pages for beep to figure that out :)

as for the runtime, the ```
time
``` command can give you that info.

The command has tons of usage info, but basically you append it to the beginning of any command you run, and it will give you the runtime of that command, for example:

If you ran this in your script:

```
aptitude update
```
you would just change it to 
```
time aptitude update
```

and it would run as normal, then give you the runtime in seconds. It gives three sets of output, real, user, and system. the real time is what really matters.

Anyway, that should give you enough to play with, enjoy

---

### Post by ngrieb on 2010-03-05
Ya, thanks. Perhaps the reason it wasn't working for me was the fact that beep is no longer installed...just checked and it was installed but I still don't hear it? Other sounds work though and I am pretty sure I have a PC speaker. Would the beep come out of the speakers or headphones if some are plugged in?

---

### Post by ngrieb on 2010-03-08
Still can't get the beep command to do anything, but the easiest way I found to do this was simply an:

&& echo -e "\a"

I was kinda hoping I could get beep to work though so I could play like a little victory tune with my finished process or maybe a fail sound when something crashes....haha. Oh well.

On a side note, there is a device option under beep, -e, that might be what I'm looking for, does any one know what this does?

---

### Post by lavinog on 2010-03-08
> **ngrieb said:**
> Ya, thanks. Perhaps the reason it wasn't working for me was the fact that beep is no longer installed...just checked and it was installed but I still don't hear it? Other sounds work though and I am pretty sure I have a PC speaker. Would the beep come out of the speakers or headphones if some are plugged in?
beep tries to come out of the pc speaker.
Some of my computers do not have a pc speaker. They instead use the sound card, but I cannot get beep to play through the card.  Ubuntu used to have a mixer, but for some reason the volume control doesn't provide this anymore.
Maybe alsa mixer might work.

---

