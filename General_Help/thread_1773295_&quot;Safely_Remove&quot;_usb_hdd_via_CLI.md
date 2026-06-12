---
title: "&quot;Safely Remove&quot; usb hdd via CLI"
date: 2011-06-01
forum: General Help
---

### Post by CharlesA on 2011-06-01
Hi,

I've got a couple external hard drives on my Ubuntu Server 10.04.2 box. One of them, a Seagate FreeAgent 2TB, powers down after it's unplugged from the USB port. The other one, a Seagate GoFlex Desk 3TB, stays spinning and doesn't power down if it's unplugged from the USB port.

The 2TB drive is USB 2.0, while the 3TB drive is USB 3.0, but I don't know if that makes a difference.

I'm looking for a way to "safely remove" it so that the device powers down and the platters stop spinning before I unplug it.

I did find a thread on the [debian forums]("http://forums.debian.net/viewtopic.php?f=5&t=52627") that was looking for the same thing, but I'm not quite sure how to tell which usb port that drive is hooked up to (since it's using an add-on USB 3.0 card). Not even sure what command would be used either.

Thanks!

---

### Post by MunkyJunky on 2011-06-02
Try the **[unmount]("http://manpages.ubuntu.com/manpages/oneiric/man8/umount.8.html")** command.

---

### Post by CharlesA on 2011-06-02
Thanks. The drive was already unmounted.

I wanted to "safely remove" it where it powers down like you do via the GUI.

I found an old thread [here]("http://ubuntuforums.org/showthread.php?t=451344"), that seemed to do the trick.

The commands that needed to be run were:

```
sudo sdparm --command=sync /dev/sdc1
sudo sdparm --command=stop /dev/sdc1
```

---

