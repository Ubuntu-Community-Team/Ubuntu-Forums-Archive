---
title: "Sound card question"
date: 2004-10-19
forum: General Help
---

### Post by madept on 2004-10-19
I'm trying out various distros in Virtual PC to decide which to actually install.
I haven't decided which distro yet, but it's going to be either Ubuntu, Gentoo, or Vidalinux.

The main reason I'm a little hesistant to install Ubuntu is that it doesn't work with my sound card, a Dell SB Live (emu10k1x).
I found this:  [https://bugzilla.ubuntu.com/show_bug.cgi?id=1435](https://bugzilla.ubuntu.com/show_bug.cgi?id=1435)

But it doesn't help much.  If I'm going to have to compile the kernel, I'll just go with Gentoo.
Is there any other way to add support for my sound card to Ubuntu?
Or will the support for it be added for 4.10 final release?

---

### Post by iwasbiggs on 2004-10-19
It seems to me that you should look at the bigger picture of which distribution you would prefer. You should have a look at what core maintenance of systems would require and then make a descision on how you want to spend your hard drive.

Is something preventing you from installing all 3 on separate partitions?

ALSA can always be patched, compiled, and upgraded later as you need it, regardless of distribution.

Maybe Dell SB Live cards use a different chipset, but my Creative SBLive has always worked with linux systems.

---

### Post by madept on 2004-10-21
I think I'll try out Ubuntu and Vidalinux and decide which I like after that.

Is there a guide anywhere to help with updating ALSA?
I tried it with Gentoo and could get it working.

The Dell/Creative SB Live uses a different chipset than Creative SB Live. :wink:

---

### Post by iwasbiggs on 2004-10-21
Not that I know of, but I don't think it'd be too much different from configure, make and install.

---

