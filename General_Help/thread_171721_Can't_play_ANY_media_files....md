---
title: "Can't play ANY media files..."
date: 2006-05-07
forum: General Help
---

### Post by pyromidget on 2006-05-07
Hey all - finally managed to get 5.10 up and running (had to use LILO as GRUB didn't like me :( ) but i've come up against a slight snag...

Any time i try to play any kind of media, i get this error (using totem as an example, but happens with anything i try):

> Totem could not play 'file:///home/martin/Desktop/Halo Soundtrack/06 - A Walk in the Woods.mp3'.

Failed to play: Could not open resource for writing.

I thought at first it might be because i was trying to play them from an NTFS volume,  so i tried copying a few directories over (the example being one of them) and giving them full r/w permission, but still no joy.

The only other thing i can think it might be is that my sound card stopped getting recognised after i installed all the win32 and gstreamer codecs from the Restricted Formats guide on the Wiki.  More in this thread:

[http://www.ubuntuforums.org/showthread.php?t=171718](http://www.ubuntuforums.org/showthread.php?t=171718)

I'm well out om my league as i'm still a newbie, but have you kindly folks got any ideas?

---

### Post by Sef on 2006-05-07
Did you download the codecs from Restricted Media?

If not, follow this link.

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by bluevoodoo1 on 2006-05-07
I have found this link...
[http://www.ubuntuforums.org/archive/index.php/t-141343.html](http://www.ubuntuforums.org/archive/index.php/t-141343.html)

(the last post seems most helpful)

---

### Post by pyromidget on 2006-05-07
[edit]  FAO Sef :) [/edit]

> The only other thing i can think it might be is that my sound card stopped getting recognised after i installed all the win32 and gstreamer codecs from the Restricted Formats guide on the Wiki. More in this threa

Yep (see above) :p

---

### Post by pyromidget on 2006-05-07
FAO bluevoodoo:

Thanks for the link - tried it, but got this:

> martin@nerthus:~$ sudo su
Password:
root@nerthus:/home/martin# killall esd
esd: no process killed
root@nerthus:/home/martin# esd &
[1] 9924
ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3948:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default
root@nerthus:/home/martin#

Any other ideas?  I really appreciate the quick replies btw :)

---

### Post by bluevoodoo1 on 2006-05-07
system > preferences > sound 

I think in Breezy there is something there to choose whether to use ALSA, Oss, etc. etc. I don't think it's in Dapper (because I can't find it!), so I can't really help. But check that out. Try different combinations.

---

### Post by pyromidget on 2006-05-07
Do you mean in the 'Default sound card' bit?

All I have there is  **MPU-401 UART**

Can't see anything about ALSA etc though. :(

[edit]

Ok, so now we're getting another new error:

> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

I'm gonna start crying soon... ](*,)

[/edit]

---

### Post by bsalt on 2006-05-07
[QUOTE=pyromidget]Hey all - finally managed to get 5.10 up and running (had to use LILO as GRUB didn't like me :( ) but i've come up against a slight snag...

Any time i try to play any kind of media, i get this error (using totem as an example, but happens with anything i try):



I thought at first it might be because i was trying to play them from an NTFS volume,  so i tried copying a few directories over (the example being one of them) and giving them full r/w permission, but still no joy.

The only other thing i can think it might be is that my sound card stopped getting recognised after i installed all the win32 and gstreamer codecs from the Restricted Formats guide on the Wiki.  More in this thread:

[http://www.ubuntuforums.org/showthread.php?t=171718](http://www.ubuntuforums.org/showthread.php?t=171718)

I'm well out om my league as i'm still a newbie, but have you kindly folks got any ideas?[/QUOTE]

I used to have the same problem, and I didn't even bother with trying to set it up myself. I searched google for Automatix and did the install that way. Automatix is even tailored for Ubuntu Breezy. It will get your audio files working, along with many other cool little things.

---

### Post by pyromidget on 2006-05-07
[QUOTE=bsalt]I used to have the same problem, and I didn't even bother with trying to set it up myself. I searched google for Automatix and did the install that way. Automatix is even tailored for Ubuntu Breezy. It will get your audio files working, along with many other cool little things.[/QUOTE]
Thanks man - Automatrix helped a lot as Breezy now recognises that i have a sound card!

Now, however when i try to play any music files i get:
> Totem could not play 'file:///home/martin/Desktop/Halo Soundtrack/07 - Ambient Wonder.mp3'.

This is an audio-only file, and there is no audio output available.

We're so close!! Any clues what it might be now?

---

