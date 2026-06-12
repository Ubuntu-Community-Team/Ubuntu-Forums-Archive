---
title: "A sound fix that seems to break itself on reboot"
date: 2011-07-09
forum: General Help
---

### Post by dwigyit on 2011-07-09
I have an MSI GX660R laptop and the sound on it plays only out of the subwoofer (so it's quiet and can't go to the higher pitches without crackling).

There is a fix which I found on the internet, which involves adding this to alsa-base.config

```
#Fix for Intel (ICH9 Family) HD Audio Controller with Realtek ALC1200 on MSI GT725
options snd-hda-intel model=targa-dig
# targa-dig	Targa/MSI
# targa-2ch-dig	Targa/MSI with 2-channel
# targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
# Headphones
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
```

Thing is, I can reboot the computer after adding it and it works perfectly - the speakers work fine and sound sounds great. But after the next reboot, sound stops working altogether and I have to remove the fix just to get the subwoofer-only sound again. Funnily enough though, I can add the fix back and reboot again and it works again for another reboot - it's very strange.

Anyone got any ideas? Thanks :)

---

### Post by dwigyit on 2011-07-13
Turns out it's not actually after every reboot that it breaks - usually takes one or two reboots before it does. Once it's broken, though, I have to reboot with the fix removed and then reboot again with it applied for the sound to work properly again. :(

---

