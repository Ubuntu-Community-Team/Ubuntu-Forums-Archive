---
title: "Alsa Mixer auto mutes speakers on startup."
date: 2011-02-09
forum: General Help
---

### Post by rhyobit on 2011-02-09
I tried posting this in beginner help but I figured I probably won't get the best response in there so I thought I'd repost here also:
Hi All,

I've got an Acer 7736 and had quite a few issues with no sound after my install of 10.10. After quite a bit of fiddling I managed to get that sorted and I now how have sound. I believe I'm using alsa although pulse also does seem to be on here. The reason I say I believe I'm using alsa is that after startup, I have no sound on speakers unless I unmute it in alsamixer.

As I understand it alsa's supposed to save your settings on logout/shutdown/reboot but this doesn't appear to be the case, and I'm not able to find any asound.conf or the like in the places they're apparently supposed to be 

Can anybody point me in the right direction?

---

### Post by wojox on 2011-02-09
After you configure alsamixer, escape and run:

```
sudo alsactl store 0
```

---

### Post by rhyobit on 2011-02-10
Thanks wojox,

I've tried something similar already, not with sudo though, just gave it a bash now and it's still muted however :(

I did notice that the software centre's installed some pulse audio stuff, is it possible there's some kind of conflict going on?  

Could having hdmi audio out hardware in addition to standard speakers be overriding the stored audio settings?

**edit**

With this as a possibility I had a further dig, I've found alsa-base.conf and tried adding the cards in according to their index at the base of the file, once done this shows as:

> # Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options 0 snd_hda_intel index =2
options 1 snd_hda_intel index=0

I've taken ID for the cards the following file, which returns:
> #cat /proc/asound/modules
0 snd_hda_intel
1 snd_hda_intel


I've added these in as described above, but I'm not sure I'm doing it correctly listing their index in the alsabase-base.conf file, have I done this correctly?  Considering they both have the same label or "name", I'm not sure how else I can differentiate between them?

---

### Post by rhyobit on 2011-02-10
Ok, I've found the following command which restores sound without editing alsa settings:

> sudo alsactl restore

I'm guessing that this indicates that alsa is saving my audio settings, just not reloading them.  I've tried adding the above command into local.rc but my settings weren't reloaded.

Entering the command manually after startup seemed to restore audio without any issue.  

So the question becomes, can anybody advise me of a way to run this command at startup, but after whatever alsa does itself at startup as I think that's likely the best work around?

---

