---
title: "external USB keyboard not working"
date: 2006-06-05
forum: General Help
---

### Post by syxbit on 2006-06-05
my desktop just broke, so i'm using my laptop as my main comp..outputting to my monitor, and using my regular keyboard and mouse.
everything works fine, but the keyboard doesn't work (it's going through my dell 2007fpw monitor's hub)
any ideas ?

---

### Post by Jussi Kukkonen on 2006-06-06
Let's see if system log says anything: run 
```
tail -f /var/log/syslog
```
and plug the keyboard in. If you get any output at that point, paste it here.

You might want to try connecting the keyboard directly, without a hub, if possible. By the way, is the hub connected to the machine through usb (no pcmcia-tricks or something)?

 Better post the model of the keyboard too, maybe someone has experience...

---

### Post by mlho on 2006-06-06
i'm having very similar problems with my external keyboard. have posted my error messages here: [http://ubuntuforums.org/showthread.php?t=189728](http://ubuntuforums.org/showthread.php?t=189728)

some people have got it to work by turning of USB legacy support in the BIOS, but that hasn't helped me.

mark

---

### Post by syxbit on 2006-06-06
i get this
although the process took ages, and seemed like it was in a loop. so i stopped it
un  6 17:15:53 SyXbiT-Duo kernel: [4294994.206000] input: Dell Dell USB Keyboard as /class/input/input606
Jun  6 17:15:53 SyXbiT-Duo kernel: [4294994.206000] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.7-3.2
Jun  6 17:15:53 SyXbiT-Duo kernel: [4294994.253000] drivers/usb/input/hid-core.c: input irq status -71 received
Jun  6 17:15:53 SyXbiT-Duo kernel: [4294994.301000] drivers/usb/input/hid-core.c: input irq status -71 received
Jun  6 17:15:53 SyXbiT-Duo kernel: [4294994.349000] drivers/usb/input/hid-core.c: input irq status -71 received
Jun  6 17:15:53 SyXbiT-Duo kernel: [4294994.397000] drivers/usb/input/hid-core.c: input irq status -71 received
Jun  6 17:15:53 SyXbiT-Duo kernel: [4294994.444000] drivers/usb/input/hid-core.c: input irq status -71 received
Jun  6 17:15:53 SyXbiT-Duo kernel: [4294994.445000] usb 5-3.2: USB disconnect, address 111

as you can see, it's a dell usb keyboard

---

### Post by cloudless on 2006-06-07
I've installed Ubuntu 6.06 on my iBook G4, and now my external keyboard is not working. When the keyboard is plugged in, I keep seeing the following message in my syslog:

Jun 7 05:06:37 cloudless-laptop kernel: [ 1630.191576] drivers/usb/input/hid-core.c: input irq status -32 received

---

