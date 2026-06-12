---
title: "why does running dmesg over and over fix my usb drives?"
date: 2010-08-25
forum: General Help
---

### Post by hydrogia on 2010-08-25
I've had problems accessing my USB drives (Canon 400D or Mini Flash Drive) on my T42; but they mount automatically when inserted into an Jaunty desktop I use at work (same OS).

While searching here to try and fix, there were lots of requests and examples of dmesg output, and as I was running dmesg over and over to see my own output, suddenly my drive was recognised and mounted (just like on the desktop).

My solution for the T42 thus far has been to run dmesg over and over again, until eventually (usually less than 5-10 times) the drives are picked up and mounted.

My question is why does this work? Isn't dmesg just a reader function? I'm fine with the way that it works because it's not too much of a concern to me, and it does work; but does this point out a specific problem that could easily be fixed just to keep from having to do this?

dmesg sample after running 3 times:
(only difference between the other 2, is the last 3 lines)

[ 1509.940405] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1510.132392] hub 1-0:1.0: unable to enumerate USB 5-device on port 3
[ 1510.324809] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1510.512308] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1510.700283] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1510.944062] usb 1-3: new high speed USB device using ehci_hcd and address 32
[ 1511.012316] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1511.200484] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1511.388414] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1511.630083] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1511.884054] usb 3-1: new full speed USB device using uhci_hcd and address 3
[ 1512.031495] usb 3-1: not running at top speed; connect to a high speed hub
[ 1512.109050] usb 3-1: configuration #1 chosen from 1 choice

---

### Post by srs5694 on 2010-08-25
I strongly suspect it's coincidental. You've got a flaky USB device that's being detected after a while, and running dmesg is just showing you when it's finally detected. As you say, dmesg just reads the kernel ring buffer; it doesn't cause the kernel to do anything to redetect hardware. (With the right options, you can adjust the size of the kernel ring buffer with dmesg, but this also shouldn't cause hardware to be redetected.)

---

### Post by hydrogia on 2010-08-26
Hmm... It might be coincidental, but if I leave the drive(s) plugged-in without running dmesg, they will never auto-mount by themselves. It only works after running dmesg a few times. For some reason USB mice seem to work right away though. Even stranger, the forementioned USB devices all work instantly on any other box (xp, mac or ubuntu), just not this laptop.

I've long suspected that the usb drives on this T42 are bunk, but at least they eventually work. Oh well, like I said, not a big issue. Just curious.

Thanks for the help!

---

### Post by srs5694 on 2010-08-26
Perhaps running dmesg is hitting the machine's disk generally (to load dmesg and related libraries, for instance), and this is causing subtle electrical changes that cause a flaky USB device to be re-registered. That's a stretch, but if you're certain it's a real effect, it's all I can think of.

---

