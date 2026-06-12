---
title: "Mythbuntu 10.10 - lost internet connectivity"
date: 2011-05-02
forum: General Help
---

### Post by el_Paraguayo on 2011-05-02
This is very strange. The internet has been working happily on my Mythbuntu machine for many months but stopped working overnight.
 
If I try to do "sudo start networking" I get a "Job failed to start" message.
 
There's also a solid orange light on the ethernet socket.
 
As it's been working for months, I don't think my interfaces config needs updating.
 
Looking at what's been updated recently on the system:
 
1) I've configured the machine to wake from USB. It was working for a couple of days so I don't believe this is the issue.
 
2) I set up wake-on-lan with ethtool. Again, this was working (although it did seem to disable wake-on-usb and required a reboot to fix)
 
3) Update to 11.04 - I said no to this, as 10.10 was working very nicely indeed.
 
 
I've disabled wake on lan and rebooted. No joy.
 
ethtool detects the ethernet controller ok and it's listed in lshw.
 
 
Does anyone have any ideas what could be going on?

---

### Post by el_Paraguayo on 2011-05-02
I tried a 10.10 LiveCD - no joy.
 
Given that I'd had IRQ conflicts with this mobo before, I tried removing the TV Tuner card.
 
Bingo! Internet back up and running.
 
Put TV tuner back in, internet still working.
 
Makes no sense to me whatsoever but I'll mark this as solved.

---

