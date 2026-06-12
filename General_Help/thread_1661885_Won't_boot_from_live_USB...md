---
title: "Won't boot from live USB.."
date: 2011-01-07
forum: General Help
---

### Post by anti-other on 2011-01-07
[FONT=Arial]Hey, what's up..

So, I'm relatively new to Ubuntu. Well, I've only been checking it out for the last day or so. Got 10.10 (Maverick Meerkat), and I thought I'd boot from live USB cuz in theory I'm led to believe that I would use less RAM being a solid state and all. I'm not totally sure how correct this is, so please advise me if this is wrong.

So, I tried like 2 programs to create a live USB with persistence, including the one that comes with Ubuntu 10.10 that I found in "System > Administration > Startup Disk Creator". When I boot from the USB it shows the Ubuntu loading screen thingy, and when I press.. anything I think, it displays the error:

**(process:365): GLib - WARNING ** get pwuid_r(): failed due to unknown user id (0)**

(Don't know if I got all the spacing in that right, but I'm sure you get the gist of it)
And it doesn't get any further that that. So I burned the ISO to a DVD and it works perfectly. I want to be able to use the USB though cuz I need my DVD writer for anything that involves CDs or DVDs or the like. Thanks for your help in advance!! ^_^[/FONT]

---

### Post by C.S.Cameron on 2011-01-07
Have you tried using UNetbootin? It's install can be made persistent

---

### Post by oldfred on 2011-01-07
There seem to be several errors related to this, some have been fixed, but may not be on the liveCD.

Do you have a floppy drive enabled in BIOS, but do not have a floppy drive? That is one recent error related.

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/649917](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/649917)

Some other fixes that may or may not apply:
syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)

---

### Post by anti-other on 2011-01-10
Hey, what's up.. ^_^

Yeah, it turns out it was the floppy drive enabled in the bios and I didn't have one thing. Thanks for the help!!

:)

---

