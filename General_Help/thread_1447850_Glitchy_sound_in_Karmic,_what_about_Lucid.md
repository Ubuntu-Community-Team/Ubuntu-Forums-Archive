---
title: "Glitchy sound in Karmic, what about Lucid?"
date: 2010-04-05
forum: General Help
---

### Post by javyn999 on 2010-04-05
Been using Ubuntu since Ibex, and one of my favorite things has been playing my backup copies of my old NES games in .rom format.

Been happily going along using FCEU and the frontend in the repositories up until this current version, Karmic.

Once I installed this version, it seems my 8 bit sound is broken.  The music and sound in FCEU is terribly glitchy, no matter how much I mess with the sampling rate.

ZSNES is even worse.

And recently, upon discovering Abandonware and Dosbox, been trying out old PC games, and same thing.

I never had any problems in ZSNES or FCEU with sound in Ibex or Jaunty.

I've googled around a bit, and it seems most people who had this problem along the way (in different versions)seemed to solve it by changing the sampling rate, either lowering it, or raising it.  Tried both to no avail here.

So, I'm assuming this problem is specific to Karmic, has anyone else experienced it, and if so, is it noted and being fixed for Lucid's upcoming release?

Thanks,

---

### Post by RedSingularity on 2010-04-05
If you want we can try troubleshooting it.

---

### Post by javyn999 on 2010-04-05
Sure, I'd appreciate that, but aside from changing the sampling rate, I'm not sure what else I could do...

Also, mednafm seems to work fine, but I have lots of saved states I made in FCEU so I'd like to stick with that one.

This is actually a big enough deal to me, that if it is not fixed in Lucid, I will downgrade back to Jaunty, heh.  Jaunty > Karmic all around anyway it seems, to me at least heh.

---

### Post by RedSingularity on 2010-04-05
Well how is the sound when you play it in other things?  Movies, Music,....etc

---

### Post by javyn999 on 2010-04-06
Flawless.  :/

---

### Post by RedSingularity on 2010-04-06
So then it sounds like a problem with just those applications.  Unfortunately i have no experience with those games so I wont be of much help.  I thought you may have had sound trouble in all your applications not just those few.  You will need to find someone who has used those games before.  Sorry.

---

### Post by lidex on 2010-04-06
Try installing this:
```
sudo apt-get install libsdl1.2debian-alsa
```
This is the version in lucid. If the command fails for you search "libsdl" in synaptic for your included version.

You'll need to reboot after, not sure if logout will work.

---

### Post by javyn999 on 2010-04-06
Thanks, it installed the package, but did not help any :(

---

### Post by javyn999 on 2010-04-07
After a bit more searching, I found that 

sudo apt-get install libsdl1.2debian-oss

fixed the sound in games in DosBox....but GFCE is still very screwed up.  Not only the sound, but the games slow down and crash :(

---

### Post by lidex on 2010-04-07
> **javyn999 said:**
> After a bit more searching, I found that 

sudo apt-get install libsdl1.2debian-oss

fixed the sound in games in DosBox....but GFCE is still very screwed up.  Not only the sound, but the games slow down and crash :(

Aha. How about these:
```
alsa-oss
oss-compat
liboss-salsa2
liboss-salsa-asound2
**libsdl1.2debian-all**
[I]This version of SDL is compiled with X11, aalib and ggi graphics
drivers and oss, esound, alsa, nas and pulseaudio sound drivers.[/I]

```

---

### Post by javyn999 on 2010-04-08
Thanks lidex!  I'll check on those when I get home from work tonight.  

Since my DOS games work fine now, and I tried mednafm, and it works fine for NES games (but not G/FCE which is in the repo, nor ZSNES in the repos), I'm assuming it's a problem with those packages and Karmic.

I will definitely try out those suggestions though!

If that doesn't work, I'll hold out hope for Lucid, and if no luck there, I'll downgrade back to Jaunty.

---

### Post by javyn999 on 2010-04-10
Unfortunately only the first two you listed were in the repos, and installing them did nothing :(

---

### Post by lidex on 2010-04-10
According to this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
you need this package:
```
libsdl1.2debian-pulseaudio
``` if you're using pulseaudio.

---

### Post by javyn999 on 2010-05-12
10.04 solved my problem. FCEU is still crappy but I don't mind using medna.  At least ZSNES is back to it's wonderful self :)

---

