---
title: "Should I use LTS or current release?"
date: 2009-11-17
forum: General Help
---

### Post by NightwishFan on 2009-11-17
I want to install Ubuntu for a friend on his machine. The machine is actually an old server from a library. It runs Windows 2000, which takes almost 15 minutes to boot because of a SCSI error that I cannot troubleshoot, as the bios password is lost. I do not remember the exact specs. I know that it has around 512mb of RAM, a 1200mhz 32-bit processor and an old ATI RAGE card.

I would like to know if anyone has any opinions on whether I should give them an LTS release, as they do not have the internet to update locally. I could then supply them with the new 10.04 LTS CD for them to update with. Or would the newer Karmic release work better until the next LTS?

Any advice would be appreciated.

---

### Post by Fire_Chief on 2009-11-17
Well, since 10.04 is not out (and not due out til April), you could give them 9.10 (current release) or 8.04 LTS. You could give them both and let them try each version to see how well it does. Lacking an Internet connection would only really be an issue if post-install updates are needed for hardware compatibility.
The SCSI error should be corrected before doing any new installs though as that will still be a problem when booting Ubuntu.

Cheers!

---

### Post by NightwishFan on 2009-11-17
I am going to use WUBI for the install, and I tested it on Jaunty. It worked as expected.

Currently they are using Xubuntu, which has a problem with Abiword using too much memory. I was going to install Gnome, as it will likely perform just as well, if not better.

I was wondering if using the LTS would be better in the long run for inexperienced users. Then they could simply move to the next LTS. Thinking about it, I am leaning toward using Hardy for now. Does Karmic have any better support for ATI cards? Sorry I do not know the exact model. It is an old ATI Rage.

---

### Post by Fire_Chief on 2009-11-17
For older cards, Karmic now uses the default radeon driver. ATI does not support the older cards in its binary driver. I suspect it will work equally well as far as the driver itself (esp if not gaming). I have had much better luck with the multimonitor setup in karmic than previous versions but that probably doesn't apply here.

---

### Post by NightwishFan on 2009-11-17
Thank you, Firechief. I think I will go with Karmic because of the better boot times and newer GIMP. That should help them a lot more.

---

### Post by lykwydchykyn on 2009-11-17
I don't see how installing Gnome is going to make Abiword use less memory.

If this weren't the release right before the next LTS, I'd say stick to the LTS.  But either way you're going to be upgrading it in April.  After that point, then I'd stick to the LTS.

---

### Post by TeoBigusGeekus on 2009-11-17
About the BIOS password
[http://www.computerhope.com/issues/ch000235.htm]("http://www.computerhope.com/issues/ch000235.htm")

---

### Post by NightwishFan on 2009-11-17
They are using Xubuntu, which has Abiword. They have some 200+ page doc files for books they wrote that take the machine to almost full lockup.

Please note they are on WUBI, which runs faster to stay in RAM and not page to disk.

OpenOffice must use a different memory strategy than abiwords doc plugin, because it does not use much at all. I am going to give them standard Ubuntu because it should give them more features at similar performance.

---

### Post by tripolitan on 2009-11-17
I would do a fresh install (not from Windows) and use LTS because (personally) I use the computer to do work and need stability and long-time-support and need not worry about "whats new" in the next upgrade that comes out only a few months after I get comfortable...

p.s. with the current LTS, you can still install the latest versions of Firefox 3.5 which now updates automagically from Mozilla and the latest OpenOffice, LimeWire, etc.

---

### Post by arnab_das on 2009-11-17
i would always recommend going for the latest version. LTS works best only for offices/work places.

if you're a home user, go for the latest version which offers loads of improvements over previous versions.

---

### Post by tripolitan on 2009-11-18
If one has the time to tinker or support someone else's PC, sure, by all means. I think it is well-documented (see, release notes/bug reports/errata) that latest versions always come bundled with untested packages, new bugs, experimental features and loads of oopses. I found that "stable" new releases are rare, in any of the major distributions.

Even LTS releases go through a rough start at the beginning, that is why I don't upgrade my LTS until the next LTS has been out for a couple of months (and has been tested in real-life situations).

Having said that, I did install Karmic on a friend's old PC but this friend does not mess with anything outside of Firefox and gEdit, needless to say, his Gnome install does not have a launcher, just a couple of icons on the desktop :0

---

