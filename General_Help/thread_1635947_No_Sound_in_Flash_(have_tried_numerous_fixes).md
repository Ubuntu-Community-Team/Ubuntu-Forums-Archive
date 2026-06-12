---
title: "No Sound in Flash (have tried numerous fixes)"
date: 2010-12-02
forum: General Help
---

### Post by Wolvenreign on 2010-12-02
Hey all.

Well, I can't seem to get sound in Flashplayer for Google Chrome, Firefox, or Opera. I've tried numerous fixes, including installing (and running) Flash-Aid by ilovelinux, reinstalling flash, etc. (I have tried both 32-bit flash and 64-bit flash.) The video runs but the sound doesn't.

Here's the current information on my Flashplayer:

```
Shockwave Flash

    File: /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r102

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

```

I'm running a 64-bit system. I lurked the forums for fixes, but nothing has worked so far.

Thanks in advance! (And here's hoping this post doesn't get swallowed like a lot of threads I make on this forum....)

---

### Post by sikander3786 on 2010-12-02
Did you try the fix from this page?

[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

(courtesy of forum member **lovinglinux**)

---

### Post by Wolvenreign on 2010-12-02
```
username@username-desktop:~$ sudo apt-get install asound-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package asound-gtk
```

This is what I get when I try to run sudo apt-get install asound-gtk.


Edit: ...Aaaaand now my sound is completely broken. Must have something to do with messing around with the sound files and not being able to finish the process.

---

### Post by philinux on 2010-12-02
Using aptitude search there is a package called asoundconf-gtk not sure if it's the package needed.

---

### Post by Wolvenreign on 2010-12-02
Well, the install on that one certainly worked.

Trying to run it, on the other hand...


```
username@username-desktop:~$ asoundconf-gtk
You need at least one ALSA sound card for this to work!

```

...wut?

This thing is trying to tell me that I do not have an ALSA sound card...despite having an ALSA sound card that was working half an hour ago.

Granted, it is pretty strange that it wouldn't let me use alsamixer, but I'm sure I used alsa and alsamixer on 10.04.

---

### Post by sikander3786 on 2010-12-02
Try restarting pluseaudio.

```
killall pulseaudio
```

Or,

```
pulseaudio -k
```

Then,

```
pulseaudio --check
```

If it is not running, press Alt + F2 and type pulseaudio to run it.

If that doesn't work, try a reboot.

---

### Post by Wolvenreign on 2010-12-02
> **sikander3786 said:**
> Try restarting pluseaudio.

```
killall pulseaudio
```

Or,

```
pulseaudio -k
```

Then,

```
pulseaudio --check
```

If it is not running, press Alt + F2 and type pulseaudio to run it.

If that doesn't work, try a reboot.

Woah! That was weird!

When I killed PulseAudio, a whole bunch of things changed about the desktop environment. I was using Gnome, then everything started popping out and changing the general look of it.

I wonder if Gnome had some dependencies on PulseAudio...?

Well, I ran PulseAudio again, but the sound still isn't working at all. I can't play mp4s, mkvs, etc, anymore.

And, of course, Flash still isn't working. Here, I'll give it a reboot and see what happens.

Edit: Well, the desktop is back to normal...but all sound is still broken.

---

### Post by Wolvenreign on 2010-12-02
Felt the need to bump this, so I'm posting rather than editing.

After reinstalling alsa and pulseaudio, still no sound. Nothing works.

Sheesh...

Edit: ```
username@username-desktop:~$ sudo /sbin/alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/david/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/david/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

```

---

### Post by sikander3786 on 2010-12-02
Hmmmm. That seems problematic.

Please follow **Part A** in this thread and try resetting Pulseaudio as mentioned there.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I have not much experienced with that stuff so if the problem persists and no other mate jumps in here, I would recommend to start a new thread under Multimedia & Video regarding your current problem.

---

### Post by Wolvenreign on 2010-12-02
Yeah, that didn't go very well. There's a whole bunch of missing directories and the like.

I'll go post under Multimedia and link back to this thread.

---

### Post by sikander3786 on 2010-12-02
> There's a whole bunch of missing directories

If you mean missing dependencies or broken packages by that, try re-installing those by,

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

Please post the output if errors are listed there. BTW, these command won't do any harm at all :-)

---

### Post by Wolvenreign on 2010-12-02
No error messages from those commands, and no fix yet.

---

### Post by Wolvenreign on 2010-12-02
Hmm...now this is odd.

I just tried Lugaru HD to see if the sound works on it...and it does! I still can't play .mp4s, etc.

It appears to me as though asound.conf is simply broken.

---

### Post by sikander3786 on 2010-12-02
Try removing asound.conf.

```
sudo rm /etc/asound.conf
```

---

### Post by Wolvenreign on 2010-12-02
> **sikander3786 said:**
> Try removing asound.conf.

```
sudo rm /etc/asound.conf
```

That's what got me into this mess to begin with. Now I don't have a replacement asound.conf.

---

### Post by sikander3786 on 2010-12-02
Normally there is no asound.conf unless you create it yourself. At least it is not on my pc.

Ok, rather than removing that file, rename it so you'll be able to restore if needed.

```
sudo mv /etc/asound.conf /etc/asound.conf.bad
```

If you need to restore,

```
sudo mv /etc/asound.conf.bad /etc/asound.conf
```

---

### Post by Wolvenreign on 2010-12-02
> **sikander3786 said:**
> Normally there is no asound.conf unless you create it yourself. At least it is not on my pc.

Ok, rather than removing that file, rename it so you'll be able to restore if needed.

```
sudo mv /etc/asound.conf /etc/asound.conf.bad
```

If you need to restore,

```
sudo mv /etc/asound.conf.bad /etc/asound.conf
```

That asound.conf file is gone. There is no backup left. I followed that first tutorial, which asked me to delete asound.conf, and I didn't make a backup.

Silly in hindsight, but I thought I was just going to be able to walk through it quickly! Grrr.

---

### Post by Wolvenreign on 2010-12-02
Hmm. Xine still works...which means I can play anything I want, really...

But DragonPlayer, MoviePlayer, VLC, Gnome MPlayer, and of course, flash video, still don't work. Games do, though.

Yeah, it's gotta be that asound.conf.

---

### Post by soad6 on 2010-12-05
I'm to assume this hasn't been fixed yet?? My question is what kind of computer is it laptop or desktop?? and if manufactured model number and all that. Second what version of adobe are you running now and im assuming Linux Ubuntu 10.10 -64 bit as your system? I will look into the issues with pulseaudio... and what all should be installed.

---

### Post by soad6 on 2010-12-05
Just wondering but mind going into synaptic and checking to see if you have 
flashplugin-nonfree-extrasound & flashplugin-nonfree installed? If not maybe installing those will fix your errors with no sound in flash... I remembered I used to have to install those when I installed flash so I could sound on Flash games like Dofus. Not sure if this helps any. If you have anymore information about the errors your getting I can try to look for other things related to them.

---

