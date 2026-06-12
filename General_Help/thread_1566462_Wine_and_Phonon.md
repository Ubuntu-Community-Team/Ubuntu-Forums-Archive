---
title: "Wine and Phonon"
date: 2010-09-02
forum: General Help
---

### Post by Ashlee on 2010-09-02
Greetings all, its been a while!

I haven't touched Ubuntu in a while due to me blowing it up last time (hey, I had fun!) and now I've installed 10.04, and have also upgraded to KDE 4.5 (I'm on Kubuntu)
Loving the updates so far, excellent job.

Now, some things have changed and I've figured most of the menus out, but I've hit a problem with Wine.

Last time, I just selected ALSA as my audio driver in both system settings and Wine, and it was fine.
Now, the only place I can find anything regarding sound is in 'multimedia' and the only option at the side is Phonon. That's new to me, looks like a new backend is being used? Sound within KDE works fine, albeit a bit stuttery (short notification sounds have their start and end cut off a few milliseconds) but Wine isn't having any of it with either ALSA or OSS selected. There is no phonon option in Wine. Looking at the backend, its Xine powered, again; no selection of that available in Wine.

Where the heck did ALSA and OSS go? 
its apparently installed:
```
ash@Genesis:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

```
and I've ran updates on alsa-utils and alsa-tools.

Typing 'alsaconf' in the commandline returns 'command not found'

lspci:
```
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)

```

I might be being incredibly dumb here, as sound drivers never were my speciality, so, sorry if I am. I can make you a pretty website if you like since that's what I do ;)

Thanks yet again for your time.

---

### Post by Ashlee on 2010-09-03
Shameless bump

---

