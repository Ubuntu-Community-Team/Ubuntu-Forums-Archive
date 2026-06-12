---
title: "No sound or video"
date: 2011-10-07
forum: General Help
---

### Post by Barney-R on 2011-10-07
Hello,

First time here, and I've got what seems like a complicated problem, but I'll keep this as brief as I can.

I've been using Ubuntu (10.10 Maverick, 64-bit) since April, regularly updated and with all the "restricted" files installed. I've also done a virus scan recently using KlamAV, which found nothing.

A few days ago I lost all sound. No system sounds. No log-in sound. Audio files (.mp3 and .wav) won't play. No sounds at all. It's as if the speakers are switched off.

In System > Preferences > Sound, on the Input tab, there's no microphone shown, though it was recognised previously.

If I try to watch a video on the internet, it's silent and the visuals are speeded up.

I can't play saved video files (.flv .mp4 .wma). Sometimes I get an error message, sometimes not. Occasionally it just plays very fast, seconds rather than minutes.

Error messages, when I do get them, can include "Disconnected: Connection terminated" and "pa_stream_cork () failed: Connection terminated". Sometimes the player (Totem?) crashes with numerous error messages like these that can't be closed, and I have to use "Force Quit".

One other detail that may or may not be significant is that the "double arrow" icon representing my broadband connection has disappeared from the top of the screen, though the connection is still working properly (I'm using it to post this).

At first I thought it must be a hardware failure as I hadn't changed any settings, but when I switch to another user account, everything works exactly as it should. It's only the main account that has the problems.

If I have to use Synaptic or the Terminal, please remember that I'm still a comparative newbie. I've used both on occasion, but please try to keep it simple. Thank you.

---

### Post by Barney-R on 2011-10-11
Seems no-one can help with this, or am I just getting impatient?

I'd appreciate any suggestions, anything that links loss of sound with loss of video. I haven't changed any settings, and nothing is muted.

The strange thing is that everything works perfectly on another "user account", so I know it's not a hardware problem, and I wouldn't have thought it was a driver problem either.

My e-mails and bookmarks are on the main account, so I have to keep transferring URLs to be able to access anything that includes sounds or videos, which considering the way the internet is nowadays, is pretty frustrating.

I'd reinstall, but I've forgotten my e-mail passwords, and I'd rather not have to re-customise everything anyway. I'm getting desperate. I hope someone can help.

It's not a memory or capability related problem either. I had this computer purpose-built less than a year ago, with an Asus P6X58D-E motherboard, i7 processor and 6GB or RAM (plus 1.3 TB total hard drive capacity).

---

### Post by Barney-R on 2011-10-11
Hello again. I managed to solve the sound and video problem. I still don't know what caused it, but in System > Preferences > Sound, the Hardware tab didn't match the Output tab. I changed it so that both referred to the same thing, and suddenly everything works again.

---

