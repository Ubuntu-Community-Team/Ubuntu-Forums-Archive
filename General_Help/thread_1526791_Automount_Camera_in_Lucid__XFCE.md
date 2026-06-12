---
title: "Automount Camera in Lucid / XFCE"
date: 2010-07-08
forum: General Help
---

### Post by thenanodude on 2010-07-08
Recently upgraded to Lucid from Karmic, and now my Canon SD780 no longer automounts as a drive.  It seems the camera is detected, according to lsusb:

```
[17010.450064] usb 1-5: new high speed USB device using ehci_hcd and address 16
[17010.602821] usb 1-5: configuration #1 chosen from 1 choice
```

and I can get f-spot (or any other program) to automatically run if I put the code in Settings -> Removable Drives and Media -> Cameras -> Command ____


However, I really just want the camera to be mounted as a drive, and have a Thunar window open, so I can copy the files I want.  Suggestions?

---

### Post by AlphaLexman on 2010-07-08
If your camera utilizes a memory or flash card, I find it easier to insert it into a usb device.

[LIST=1]
[*]It saves battery power in your camera.
[*]It [should] automatically detect your memory/flash card and [hopefully] mount it.
[*]Allows drag and drop to copy pics/files.
[/LIST]

---

### Post by thenanodude on 2010-07-08
> If your camera utilizes a memory or flash card, I find it easier to insert it into a usb...

Actually, it has an SD memory card that fits into a slot on my laptop, which is how I have had to access the pics.  I was just mostly curious about how to have the camera automounted, and slightly annoyed that it used to work, and no longer does.  Every time I upgrade, it seems there is always something that fits into that category!

---

### Post by AlphaLexman on 2010-07-08
You are probably having an '/etc/fstab' issue with mounting.

Check out [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by shosto on 2011-07-10
My wife has a similar problem. Her camera is sometimes automounted and others times it isn't. Did some research and came up with a small shell script to use with nautilus to mount it, when automount fails. Instructions are contained in the script itself.

---

