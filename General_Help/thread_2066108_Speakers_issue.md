---
title: "Speakers issue"
date: 2012-10-03
forum: General Help
---

### Post by gennatolls on 2012-10-03
I recently upgrade my cheap pc speakers to some studio monitors. I now have some pretty annoying interference sounds coming from them.  I have a wireless mouse/keyboard combo that is causing 70% of that but when that is unplugged and powered off I'm still getting some interference. The speaker cable is plugged in to the back of my MB (not using a DAC here) which is obviously pretty close to my power supply.  The interesting thing is on reboot the noise stops and is fine while in the BIOS, but once Ubuntu gets about half way through the boot, the same interference noise starts back up. This made me consider if its some faulty driver.

Any ideas here? 
I'm kind of sick that my new speakers wont work properly with my Ubuntu install :(



Useful info:
I don't have any interference noises when using my Bose Quiet Comfort 15 s.

The cord connecting the speakers works flawlessly on my macbook under OS X and 12.04 so I think I can eliminate that. 

ETA: I have also tried both the front stereo connector as well as the one on the back of the MB with no avail

```
cat /proc/asound/card0/codec* | grep Codec
```Output:
```
Codec: Realtek ALC892
```

---

### Post by gennatolls on 2012-10-08
Update 1:

Plugged in an adapter to eliminate the ground on my pc's plug. I'm thinking I may have a sub par motherboard and the on board sound card starts making noise when Ubuntu boots once also/pulse daemons start. This is the only thing I can think of so far. I'll be upgrading to a DAC and use the optical out the eliminate any noise from and improperly grounded system.

---

