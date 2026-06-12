---
title: "Ongoing problems booting 10.04 (Lucid LTS)"
date: 2011-05-15
forum: General Help
---

### Post by SixStringSW on 2011-05-15
I'm running Lucid (AMD64) on a 2009 Mac Mini, 6 GB RAM. Single boot system; not running rEFIt or anything.

About 80% of the time, it fails to boot. I disabled the fancy Plymouth graphics startup, which seemed to help a bit, but it's still unacceptable.

Typical sequence: I turn on the Mac, I get a blank white screen for 60-90 seconds (WHY does this take so long??), then the screen goes black and the GRUB screen appears. I select the most recent kernel (.32), or it times out, then the screen goes blank, I get a brief flash of a text cursor in the upper left corner, and it never returns. Just a blank, black screen. 

During a successful boot, the GRUB screen clears and I immediately get a stream of text as it goes through all the boot-up sequence. But most of the time, I get nothing but blackness after GRUB.

It seems to help if I unplug the Mac for 20 seconds and reboot.

Jaunty booted great: just a few seconds to GRUB, and about 30 more to get to login. And it never--never--failed to boot. Even at its best, Lucid takes a good couple of minutes. But 80% of the time, it doesn't boot at all.

Any ideas what I can do to troubleshoot this? Would upgrading to 10.10 or 11.04 be of any value?

---

### Post by mörgæs on 2011-05-15
> **SixStringSW said:**
> Would upgrading to 10.10 or 11.04 be of any value?

It is a good idea to try 10.10 for comparison, but I would recommend a fresh install rather than an upgrade.

Remember to have wired internet access while installing.

---

