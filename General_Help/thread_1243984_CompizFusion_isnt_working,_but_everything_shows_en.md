---
title: "Compiz/Fusion isnt working, but everything shows enabled?"
date: 2009-08-19
forum: General Help
---

### Post by PsychedelicWonders on 2009-08-19
OK I recently got all 4 of my monitors to work in conjunction with each other, but my Compiz Fusion effects have been disabled.  3D cube etc.

I'm in Compiz Settings manager & everything still shows enabled & active... but yet my dock & 3D cube arent there?

What do I do?

---

### Post by ptsubin on 2009-08-19
Are you sure the Visual effects were set to Extra when you have started ccsm?

---

### Post by PsychedelicWonders on 2009-08-19
> **ptsubin said:**
> Are you sure the Visual effects were set to Extra when you have started ccsm?

ahh, might not... how do I do that again?

---

### Post by ptsubin on 2009-08-19
Right click on desktop, choose change desktop background, and then click on visual Effects tab..

---

### Post by PsychedelicWonders on 2009-08-19
Now I get this weird error message:  The Composite Extension is not available

Thoughts?

---

### Post by ptsubin on 2009-08-19
[http://ubuntuforums.org/showthread.php?t=510733](http://ubuntuforums.org/showthread.php?t=510733)

[http://forum.compiz-fusion.org/showthread.php?t=5468](http://forum.compiz-fusion.org/showthread.php?t=5468)

And google gave me many results. I think second is good.

---

### Post by PsychedelicWonders on 2009-08-19
Ok, I followed the 2nd one, this code:

```
sudo apt-get install xserver-xgl
```

And it seems to have screwed everything up?

A window will show normal on 2 of the monitors, & then when I drag it onto the other 2 monitors, everything in the window goes black?

I cant see icons or things highlighted?

How do I reverese this?

It did help enable Compiz Fusion though.  But still has something wrong with it.

My dock never showed back up again either.

---

### Post by PsychedelicWonders on 2009-08-19
I just tried to edit my Nvida X Server settings and I get this error:

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server.

I had to retype the message as it wouldnt copy or paste, so I think those are apostrophies.

---

### Post by ptsubin on 2009-08-19
I suggest you say bye bye to Compiz. and sudo apt-get purge xserver-xgl. There are things more important than a rotating desktop or wobbly windows. Or wait till some experts come here.. sorry.. i can be of no more help.. wait, what is your graphics card?

---

### Post by ptsubin on 2009-08-19
So this might be the problem, also get updated xserver drivers from launchpad PPA. Jaunty default ones have some probs. Now do what it said you, add PPa repos. update drivers. and that may get fixed.

---

### Post by PsychedelicWonders on 2009-08-19
Why would I say bye to compiz?

I've seen this work on others systems.

Ok I just ran this...

psychedelicwonders@JohnnyScience:~$ sudo apt-get purge xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19 libglitz-glx1 libglitz1
  linux-headers-2.6.24-19-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xserver-xgl*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 5226kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 184327 files and directories currently installed.)
Removing xserver-xgl ...
Purging configuration files for xserver-xgl ...
psychedelicwonders@JohnnyScience:~$ 


So what happens now... does Nvidia X Server settings just fall back into place?

How do I get that back?

---

### Post by PsychedelicWonders on 2009-08-19
> **ptsubin said:**
> So this might be the problem, also get updated xserver drivers from launchpad PPA. Jaunty default ones have some probs. Now do what it said you, add PPa repos. update drivers. and that may get fixed.

What might be the problem?

How do I update Xserver drivers from launchpad PPA?

Everything is kinda like before I rane that xgl code, but when I drag a window from screen to screen, it gets really blurry & distorted.  That never happened before.

I'm running a 9600 GT & a 9800 GT & also have 8g of ram.

---

