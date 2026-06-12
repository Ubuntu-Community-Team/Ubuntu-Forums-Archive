---
title: "&quot;Please do not remove the media&quot; message never goes away"
date: 2011-11-16
forum: General Help
---

### Post by bkline on 2011-11-16
How are we supposed to know when it is safe to turn off an external drive when Ubuntu puts up the message "Writing data to device. There is data that needs to be written to the device ... before it can be removed. Please do not remove the media or disconnect the drive" and leaves it on the screen forever?

---

### Post by dcstar on 2011-11-17
> **bkline said:**
> How are we supposed to know when it is safe to turn off an external drive when Ubuntu puts up the message "Writing data to device. There is data that needs to be written to the device ... before it can be removed. Please do not remove the media or disconnect the drive" and leaves it on the screen forever?

You **wait** for the data to be written, or basically guarantee a corrupted drive by removing it before it disappears.

---

### Post by salemhouda on 2011-11-17
Run this command
```
$sudo sync
```

---

### Post by bkline on 2011-11-17
> **dcstar said:**
> You **wait** for the data to be written, or basically guarantee a corrupted drive by removing it before it disappears.

Well, I did wait - for days - and the message never went away.  I removed the drive, shut down the system, reattached the drive, and ran a recursive diff over the files which had been copied, and not a byte was different.  I suspect that Ubuntu just forgot about removing the message.

---

### Post by bkline on 2011-11-17
> **salemhouda said:**
> Run this command
```
$sudo sync
```

Thanks for the tip!  Just what the doctor ordered.

---

### Post by 3rdalbum on 2011-11-17
Yes; if you run the 'sync' command, it will flush all the buffers to their destinations. When the terminal prompt appears again and you can type in more commands, that means that everything is up-to-date on all disks, and the device can be removed.

---

### Post by dcstar on 2011-11-18
> **bkline said:**
> Well, I did wait - for days - and the message never went away.  I removed the drive, shut down the system, reattached the drive, and ran a recursive diff over the files which had been copied, and not a byte was different.  I suspect that Ubuntu just forgot about removing the message.

In that case then you may want to report it as a bug, because it is not supposed to be like that.

If there is a bug and the maintainers never get notified, then it will probably never get fixed.

---

### Post by bkline on 2011-11-18
> **dcstar said:**
> In that case then you may want to report it as a bug, because it is not supposed to be like that.

If there is a bug and the maintainers never get notified, then it will probably never get fixed.

Responsiveness for bug reports I've filed in Launchpad (and I'm a developer myself, so I have a fairly good idea of what goes into a useful bug report) has been spotty.  In this case since I have a reasonable workaround, so there's not as much incentive.  Still, it's the right thing to do, so thanks for the nudge. :)

---

### Post by bkline on 2012-05-12
> **dcstar said:**
> ... you may want to report it as a bug ....

[https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/998573](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/998573)

---

### Post by Jose Catre-Vandis on 2012-05-12
I occasionally get this problem when, for example playing an audio file off a stick. Playback maybe finished, but audacious still has its hooks in the file, so won't allow the stick to be removed. Closing down audacious and thunar, usually does the trick. Maybe the same/similar for you ?

---

### Post by bkline on 2012-05-12
> **Jose Catre-Vandis said:**
> I occasionally get this problem when, for example playing an audio file off a stick. Playback maybe finished, but audacious still has its hooks in the file, so won't allow the stick to be removed. Closing down audacious and thunar, usually does the trick. Maybe the same/similar for you ?

I wish it were that straightforward.  I get this behavior no matter what I do with the device, including nothing at all.  In other words, the following sequence will leave me with the permanent injunction to leave the memory stick alone forever:
[LIST=1]
[*]Insert device in USB slot
[*]Right click on desktop icon for the device
[*]Select "Eject"
[*]Receive instructions not to remove the device
[/LIST]

---

### Post by wilee-nilee on 2012-05-12
> **bkline said:**
> I wish it were that straightforward.  I get this behavior no matter what I do with the device, including nothing at all.  In other words, the following sequence will leave me with the permanent injunction to leave the memory stick alone forever:
[LIST=1]
[*]Insert device in USB slot
[*]Right click on desktop icon for the device
[*]Select "Eject"
[*]Receive instructions not to remove the device
[/LIST]


If you are loading the external with fstab you need to unmount with the terminal.

---

### Post by bkline on 2012-05-13
> **wilee-nilee said:**
> If you are loading the external with fstab you need to unmount with the terminal.

There's nothing in /etc/fstab for this device.  The icon for the device appears on the desktop through some lower-level magic.

---

### Post by Zerberro on 2012-05-13
Yes, you are right!

---

### Post by flemur13013 on 2012-05-13
This is a bug. "sync" doesn't fix it.

1: Copy a 300MB file from HD to SD card. (w/thunar).

2: It shows a fast copy, ending with "1 second left" for about 10 seconds.

3: Run "$ sync" in a terminal while it's copying: sync doesn't return until just after the copy-info box goes away.

4: After sync returns, w/thunar do "Eject volume" - you get the "Writing data to device" msg.

or simply:

**Put in an SD card and then "Eject" it: you still get the "Writing data to device" even though no data was written.**

I've found that ignoring the message works well.

---

### Post by rai4shu2 on 2012-05-13
> **bkline said:**
> There's nothing in /etc/fstab for this device.  The icon for the device appears on the desktop through some lower-level magic.

I think what you're describing is the job of Thunar-volman. That would be the logical choise of package to file a bug against. (I've never had the problem, though.)

---

### Post by bkline on 2012-05-13
> **rai4shu2 said:**
> I think what you're describing is the job of Thunar-volman. That would be the logical choise of package to file a bug against. (I've never had the problem, though.)

Thanks for the suggestion.  I chose the package I filed the bug against based on the fact that the dialog window in question has "xfdesktop" in the title bar.

---

### Post by bkline on 2012-05-17
> **bkline said:**
> Thanks for the suggestion.  I chose the package I filed the bug against based on the fact that the dialog window in question has "xfdesktop" in the title bar.

The result of the bug is a "won't fix" from the xfdesktop4 maintainers.  Apparently even though "xfdesktop" is in the title bar the package responsible for the unwanted behavior is actually notify-osd.  (I don't completely understand why the title bar says what it does if that's true, but that only one of hundreds of things I don't understand about the desktop ecosystem.)  I was told that notify-osd is only given thorough testing with Unity, which I'm not using, and I was advised to replace notify-osd with xfce4-notifyd.

So many moving parts! :-)

---

### Post by rai4shu2 on 2012-05-17
That would explain why I've never seen that (I have xfce4-notifyd, not notify-osd).

---

