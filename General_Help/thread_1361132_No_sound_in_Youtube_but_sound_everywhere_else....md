---
title: "No sound in Youtube but sound everywhere else..."
date: 2009-12-21
forum: General Help
---

### Post by wotsit on 2009-12-21
Hmm yesterday it was working fine, afaik I haven't really done anything since then...

Amarok works fine, I've updated, umm yeah that's it I suppose...

But It's getting somewhat annoying.

I've tried running the youtube file from /tmp in vlc but still no sound

Should I reinstall flash? I downloaded it from the adobe site, how do I reinstall?

---

### Post by steviefordi on 2009-12-21
Make sure the video isn't muted. This caught me out once - flash video often has a volume/mute control of it's own around the screen somewhere where the video is displayed.

---

### Post by s.fox on 2009-12-21
Hello.

Could you try this?

```
sudo apt-get install libflashsupport
```

Hope this helps.

-Silver Fox

---

### Post by wotsit on 2009-12-21
yeah volume in the player is highest it'll go.

```
Package libflashsupport is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  flashplugin-nonfree-extrasound
```

i already have that installed.

keep 'em coming

---

### Post by steviefordi on 2009-12-23
It may be that the sound from your flash player is going to the wrong channel/device or is muted in the sound server. I can't remember exactly how to do this but there is a utility that allows you to direct sound streams from applications to different devices.

Run the pulseaudio device chooser. It's on the Applications > Sound menu, and it may be called something similar to device chooser. (If you're running something older than Jaunty you may have to install it via sudo apt-get padevchooser).

When running, an icon will appear on your main gnome panel, probably near the clock. Click (may be right-click) on the icon and select volume control.

Now play a youtube video. You should see the sound stream visually represented on the playback tab of the device chooser. Whilst it's playing you can adjust the volume for this application, and/or redirect the stream to another device.

Hope this helps..

---

