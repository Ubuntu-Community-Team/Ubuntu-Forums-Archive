---
title: "No sound after upgrade to 9.10 Kermic K"
date: 2009-11-04
forum: General Help
---

### Post by cogvos on 2009-11-04
Dear all,

Just upgraded to 9.10 after lots of hassle with 9.04. Looks OK, sloower to start though and flashed some odd stuff re disks not being present (hey they are external usb ones!) but what the hey.

Anyway my main problem is that I have lost all sound. I have a silent Koala. Even the alerts are silent, zilch. The sound is ATI on board (IXB SB400 AC'97 sound controller, ACL658D soundcard). This worked on 9.04 but is mute now. (Except that I checked the mute and it isn't! The volume is up there is just no sound anywhere.

Any ideas?

<edit> portions of dmesg that might help?

[    0.919527] device-mapper: uevent: version 1.0.3
[    0.919619] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.919697] device-mapper: multipath: version 1.1.0 loaded
[    0.919699] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.919827] EISA: Probing bus 0 at eisa.0
[    0.919848] Cannot allocate resource for EISA slot 4
[    0.919867] EISA: Detected 0 cards.
[    0.919913] cpuidle: using governor ladder
[    0.919915] cpuidle: using governor menu
[    0.920396] TCP cubic registered
[    0.920563] NET: Registered protocol family 10
[    0.920987] lo: Disabled Privacy Extensions
[    0.921281] NET: Registered protocol family 17

which suggests it can't find a sound card and then almost at the end

[   10.615762] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17

Not sure if this is the sound card? Its just above Eth0...

---

### Post by khelben1979 on 2009-11-04
I recommend that you post how it looks like with your sound bars using [Alsamixer]("http://en.wikipedia.org/wiki/Alsamixer")gui.

My guess is that Ubuntu Karmic hasn't loaded the appropiate sound module from your Linux kernel and if this is true, you can fix this by either using the command insmod or [modprobe]("http://en.wikipedia.org/wiki/Insmod") to manually load the sound module from your Linux kernel. Use ```
man modprobe
``` if you feel uncertain on how to use the command.

Check up what module to use by looking from [ALSA Soundcard Matrix]("http://www.alsa-project.org/main/index.php/Matrix:Main").

---

### Post by Plumtreed on 2009-11-04
Since you have upgraded it may be wise to make sure you have the right kernel loaded. It happens sometime on an upgrade and it will cause sound and other things to fail. 

Check via the System Monitor or in Grub at boot up. You should be in 2.6.31 -14

---

### Post by coldsystem on 2009-11-05
Link  :  [http://unixmen.com/linux-tutorials/documentations-a-howto/524-ac97-audio-controller](http://unixmen.com/linux-tutorials/documentations-a-howto/524-ac97-audio-controller)

---

