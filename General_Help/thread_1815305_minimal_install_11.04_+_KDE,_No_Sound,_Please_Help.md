---
title: "minimal install 11.04 + KDE, No Sound, Please Help."
date: 2011-07-31
forum: General Help
---

### Post by xekon on 2011-07-31
I have done a minimal install of 11.04 and installed KDE (4.6.5)

[http://ubuntuforums.org/showthread.php?t=1815299](http://ubuntuforums.org/showthread.php?t=1815299)

I have everything up and running and have installed all the application that I use.

The only hangup that I have run into is that I cannot get my sound to work. It is onboard sound(ALC889A) and works in both 10.10 and 11.04 ubuntu-desktop version. The motherboard is a GA-EP45-UD3P (rev 1.1)

So I am thinking there is just something that needs to be installed or configured.

So far I have installed medibuntu, pulseaudio, and also the xine and vlc backends for phonon

I have tried different preferences and settings in the phonon sound settings but I cannot get any sound no matter what I try.

I don't care what method I have to take to get sound working. I just got good working sound. right now I am reading all sorts of things I could install or try but I would hate to screw around installing all sorts of things and end up making even more of a mess.

Any help is greatly appreciated.

---

### Post by ajgreeny on 2011-07-31
All I can suggest is that you try adding **kubuntu-desktop** package and see if that adds any other packages that give you sound.

---

### Post by nothingspecial on 2011-07-31
Do you have alsa installed?

---

### Post by xekon on 2011-07-31
Yes, I ended up making a mess of things by installing and uninstalling and configuring so many sound packages and options.

I reinstalled, and then I installed kmix, and found that my volumes were all turned down, that was the only problem.

Everything seems to be working great now.

---

### Post by k3n on 2012-01-25
There are two mixer programs that solved my issue by revealing a muted channel. My Lenovo T61P seems to mute itself whenever the laptop suspends or hibernates. I appreciate that I can just launch these from a terminal.
  
In alsamixer muting is controlled by highlighting the master channel and pressing the 'm' key. In kmix, click on the speaker icon to unmute your playback device. 

Try alsamixer or kmix early in your troubleshooting, they're less risky than adding repositories and re-installing every audio package. If you need to get serious about it, follow a guide like this: [http://help.ubuntu.com/community/SoundTroubleshootingProcedure](http://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

