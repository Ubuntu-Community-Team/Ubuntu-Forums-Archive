---
title: "No sound in Lubuntu, even with open formats."
date: 2012-09-01
forum: General Help
---

### Post by jerm1027 on 2012-09-01
I have Lubuntu 12.04 64bit (latest updates installed) on my Acer Aspire One AO722 and I have no sound. Period. 

This is particularly puzzling because I'm not using any proprietary formats either. When trying to play music, GNOME MPlayer doesn't play, Audacious spits out an ALSA error about no suitable mixer element found, and Rhythmbox just crashes when trying to play audio. My entire music library is encoded with Vorbis (.ogg), and even when watching YouTube in HTML5, I still get no sound (though video works).

My understanding is this stuff is suppose to work out of the box. What's the problem here?

Also, I'm trying to avoid proprietary software as much as possible.

---

### Post by river226 on 2012-09-01
well obvious (and sorry if this offends), are you sure nothing is muted. sometime the mixer is funky:

[http://manpages.ubuntu.com/manpages/gutsy/man1/amixer.1.html](http://manpages.ubuntu.com/manpages/gutsy/man1/amixer.1.html)

otherwise this may be a similar issue to what I encountered when I tried Lubuntu and I would like to see the solution.

---

### Post by cwsnyder on 2012-09-01
[https://wiki.archlinux.org/index.php/Acer_AO722-BZ454](https://wiki.archlinux.org/index.php/Acer_AO722-BZ454) lists some of the problems found running the Arch Linux system on the AO722, including fixes for sound and a complete listing of hardware for that version of the AO722 to see if you should expect similar problems.

---

### Post by jerm1027 on 2012-09-01
> **cwsnyder said:**
> [https://wiki.archlinux.org/index.php/Acer_AO722-BZ454](https://wiki.archlinux.org/index.php/Acer_AO722-BZ454) lists some of the problems found running the Arch Linux system on the AO722, including fixes for sound and a complete listing of hardware for that version of the AO722 to see if you should expect similar problems.

Well, the guide worked, specifically this part:> Initially, audio doesn't work, except for beeping. The problem may be corrected by editing /usr/share/alsa/alsa.conf and replacing every instance of card 0 with card 1.

Thanks for the help.

---

