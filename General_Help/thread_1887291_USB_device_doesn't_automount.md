---
title: "USB device doesn't automount"
date: 2011-11-26
forum: General Help
---

### Post by NautiusMaximus on 2011-11-26
If I plug a USB device into my computer, it doesn't automatically mount. It gets detected without problems, and if I go to "Computer", I can see it there and mount it manually.

Is it possible to have it mount automatically as soon as I plug it in?

I've found one or two other threads about this. One suggested that you should check the output of this command:

```
gconftool-2 -g /apps/nautilus/preferences/media_automount
```

The output I got was "true", so I guess that isn't the problem. What else can I check?

I'm using Ubuntu 11.04.

Thanks
NM

---

### Post by dcstar on 2011-11-26
> **NautiusMaximus said:**
> If I plug a USB device into my computer, it doesn't automatically mount. It gets detected without problems, and if I go to "Computer", I can see it there and mount it manually.

Is it possible to have it mount automatically as soon as I plug it in?

I've found one or two other threads about this. One suggested that you should check the output of this command:

```
gconftool-2 -g /apps/nautilus/preferences/media_automount
```

The output I got was "true", so I guess that isn't the problem. What else can I check?

I'm using Ubuntu 11.04.

Thanks
NM

Look at the Media settings in the Nautilus Preferences.

---

### Post by NautiusMaximus on 2011-11-27
Thanks for that suggestion, but that doesn't seem to work.

If I go to the media settings in Nautilus preferences as you suggest, I have settings for various types of media, but nothing for a USB device. The closest is "music player" (and in fact this particular USB device is an MP3 player, although I'd like to have something that would work for any USB storage device), but even if I set the action for that to "Open folder", it doesn't result in anything different happening when I connect the device.

Anything else I could try?

Thanks
NM

---

### Post by NautiusMaximus on 2011-12-03
Well, that's a bit odd. Without my having done anything different, it now works. I did apply a bunch of updates earlier today, so maybe there was a bug that's been fixed with the latest updates. That's the only thing I can think of.

---

