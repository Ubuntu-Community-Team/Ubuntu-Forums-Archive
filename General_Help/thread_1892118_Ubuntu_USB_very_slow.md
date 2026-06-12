---
title: "Ubuntu USB very slow?"
date: 2011-12-07
forum: General Help
---

### Post by snakeman21 on 2011-12-07
So I've been using Mint for about 2 years, and recently switched back to Ubuntu at the request of my wife, who prefers it, and to be honest, I missed Ubuntu as well.  We downloaded Natty so we could revert to GNOME.  

But here's something strange.  I have a Seagate 1TB portable HD that I use for my backup.  It is USB 3.0.  When we were using Mint, it transfered data at about 29 to 32 MB/sec... Not bad.  Now, since going back to Ubuntu, it only transfers at 15 MB/sec... It is very frustrating.  What gives?

---

### Post by Mark Phelps on 2011-12-07
Looks like, with Ubuntu, you've dropped from USB 3.0 speeds to USB 2.0 speeds.

I'm using USB 3.0 on my PC with 11.10 -- and it, too, functions at USB 2.0 speeds, even though with Win7, I get USB 3.0 speeds.

---

### Post by oldtimer7777 on 2011-12-07
> **Mark Phelps said:**
> Looks like, with Ubuntu, you've dropped from USB 3.0 speeds to USB 2.0 speeds.

I'm using USB 3.0 on my PC with 11.10 -- and it, too, functions at USB 2.0 speeds, even though with Win7, I get USB 3.0 speeds.

I have the same issue. Never tested Mint to see if that would speed things up.  Try posting your question on the Mint Forums as well to see what they did differently to make this work faster. I would love to know too.

---

### Post by WorMzy on 2011-12-07
At a guess, the Ubuntu kernel isn't compiled with the xHCI module (CONFIG_USB_XHCI_HCD | xhci-hcd), probably because it's still experimental. Without that module, you can't use USB3.0.

---

### Post by seawolf167 on 2011-12-07
> **Mark Phelps said:**
> I'm using USB 3.0 on my PC with 11.10 -- and it, too, functions at USB 2.0 speeds, even though with Win7, I get USB 3.0 speeds.

Aye, exact same issue for me as well. Not too big a deal for me though, if I have something large to move I'll just hook up through an eSATA port.

---

### Post by cortman on 2011-12-07
Seems as if USB speeds have been a bug with Linux for a while...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197762?comments=all]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197762?comments=all")

---

### Post by snakeman21 on 2011-12-07
What I don't understand is that Mint is, for all intents and purposes, Ubuntu with some different software thrown in.  Whatever is included in Mint that allows my awesome transfer speeds should work fine on Ubuntu if I only knew what it was.

---

