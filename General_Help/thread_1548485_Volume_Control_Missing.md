---
title: "Volume Control Missing"
date: 2010-08-08
forum: General Help
---

### Post by coljohnhannibalsmith on 2010-08-08
I've read most of the other posts and none of the offered solutions work for me.

Hello, 

I'm currently using Lucid Lynx x64 and have lost my volume control icon.  Actually what really happened is a little more complicated.

After I installed Lucid on my Laptop and reloaded my media files, I discovered that my WMV files would not play in either "Movie Player" or "VLC."  I remedied this problem by installing MEDIBUNTU and the x64-codecs.  After doing this I discovered that neither Movie Player nor VLC would run while Amarok was running.  I found the following thread, which suggested "purging" "Pulse Audio," which doesn't seem to play well with  ALSA, and set everything to use ALSA only:

[http://ubuntuforums.org/showthread.php?t=1525768&highlight=amarok](http://ubuntuforums.org/showthread.php?t=1525768&highlight=amarok)

Sure enough, this fixed the problem; however after doing this I accidentally removed the indicator applet which contained the "volume control" applet, while trying to move some things around on the Task Bar.  Things then became very murky indeed.  The only fix for this, that worked for me, was to install "indicator-applet-sound," which reinstalls Pulse Audio taking me back to where I started, with the application conflicts between Amarok, Movie Player and VLC.  So, I purged Pulse Audio again and added the "gnome-alsa-mixer" icon to the Task Bar, which gave me a working volume control; but boy is this "butt ugly."  I've also noticed that Lucid's sound control applet won't work without Pulse Audio installed, neither will "gnome-control-center's."  This has been a very ugly "hack" just to get my apps to work together.

I supposed that Canonical will eventually fix "some" of the bugs I've mentioned, then I suppose I can try to reinstall Pulse Audio at some unknown point in the future; but until then, does someone have a more reasonable work around?  I've Googled for a "stand alone" volume control app, that doesn't require Pulse Audio, but I can't seem to find one.

Also, is there a way to keep Pulse Audio installed and just "bypass it," or to "turn off" Lucid's dependence on it for control and indicator functionality?

BTW, I have added "gnome-volume-control-applet" to System>Preferences>Startup Applications and have verified using Terminal that it is indeed running, but for some reason it doesn't want to display in the indicator applet, which may be related to my having purged Pulse Audio.


Any help appreciated.


Thanks Hannibal

---

### Post by dino99 on 2010-08-08
is pavucontrol or pavumeter installed ?

---

### Post by coljohnhannibalsmith on 2010-08-08
No sir,

Neither of those are installed.

---

### Post by kleinebre on 2010-09-14
> **coljohnhannibalsmith said:**
> I've read most of the other posts and none of the offered solutions work for me.

I have added "gnome-volume-control-applet" to System>Preferences>Startup Applications and have verified using Terminal that it is indeed running, but for some reason it doesn't want to display in the indicator applet, which may be related to my having purged Pulse Audio.

Any help appreciated.

Thanks Hannibal

Didn't you also ask this on Launchpad?
In any case, I had the same problem and switched to Volti by Milan Nikolic. The version 0.2.2 currently online does not yet support soundcards with independent left/right channels for master volume, but I've tweaked it so my M-Audio 2496 works with it perfectly now. I've submitted the patch to Milan so it should be available to the general
public Real Soon now.

Alternatively, if you run Compiz, you can define key bindings 
(e.g. ctrl+ and ctrl-, or if you have a fancy keyboard just assign
the volume buttons...) to run volume-up and volume-down scripts
such as the following:

#!/bin/bash
# this is /usr/bin/volmin for M-audio 2496
/usr/bin/amixer sset DAC,0 3- unmute
/usr/bin/amixer sset DAC,1 3- unmute

#!/bin/bash
# this is /usr/bin/volplus for M-audio 2496
/usr/bin/amixer sset DAC,0 3+ unmute
/usr/bin/amixer sset DAC,1 3+ unmute

If you have an onboard soundcard which does not split left/right channels, you will need only one line per script. 
In most cases, you will have to replace DAC by the name of your 
master output channel (you can run alsamixer to see what it should 
be).

Hope this helps,

Best,
Marc

---

### Post by coljohnhannibalsmith on 2011-03-30
Forunately, this was fixed in Maverick.

Solved!

---

### Post by ladasky on 2011-03-31
> **coljohnhannibalsmith said:**
> Forunately, this was fixed in Maverick.

Solved!

Alas: not in **_my_** installation of Maverick.  I just upgraded from Karmic, and lost the volume control on my top menu bar.  How do I put it back?  :confused:

---

### Post by coljohnhannibalsmith on 2011-04-12
Sorry to hear that,

I backed up my data and did a "bare-metal" install of Maverick.  I didn't have that problem again.  Since you upgraded, there may be some packages left-over from Karmic.  This could be what's causing your problem.

I know what a headache it's going to be; but I have to suggest the bare-metal solution...

In the meantime...

I recommend installing "gnome-alsa-mixer" with Synaptic Package Manager, and then adding it to the Task Bar. This will give you a working volume control...


BTW, here's a way to make your rebuild, "less" of a headache:


1. Launch Synaptic Package Manager.

2. Select File > Save Markings As... > "your file-name here"
 
3. In the lower left-hand corner, select "Save full state, not only changes."

4. Save the file to the Desktop; then transfer it to a "flash-drive."

I usually name mine "Synaptic_Full_State."

When you reinstall Maverick, reverse the proceedure.  This allows you to reload 'all' of your applications and packages 'automatically,' without having to select them manually and individually, which I wouldn't wish on anyone.

Also, copy your software sources to a text file.  That way you can reload these as well.



Good Luck, Hannibal

---

### Post by coljohnhannibalsmith on 2011-04-13
Re: the ***Bare-Metal*** reinstall/rebuild I outlined in the previous post.  I'm attaching both of these files from one of my systems, to better illustrate this...


Hannibal

---

