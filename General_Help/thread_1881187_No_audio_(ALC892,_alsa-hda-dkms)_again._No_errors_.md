---
title: "No audio (ALC892, alsa-hda-dkms) again. No errors or misconfiguration."
date: 2011-11-15
forum: General Help
---

### Post by quequotion on 2011-11-15
Just yesterday I managed to fix having no sound by hacking a lot of text files in /var/lib/dpkg/info and getting **dpkg-reconfigure -a** to work. It took several hours.

Today, I once again have no audio and reconfiguring doesn't fix it anymore.

Internally, everything seems to be fine.

Alsa recognizes the card.

Pulseaudio recognizes the card.

Nothing seems to indicate the card is broken or modules have not been loaded properly.

All of my configuration options seem to be correct, including files in /etc/.

pavumeter even shows audio levels whenever a sound plays.

No actual sound is coming out of the card.

Since there was an update today, I tried downgrading the alsa-hda-dkms package to the previous version and also the version previous to that but there was no change. The default drivers in the kernel do not work.

Any ideas?

---

### Post by quequotion on 2011-11-15
I had this working for a while after following the instructions in the Multimedia forum, but then sound went away again.

Each new fix works only once and then never works again.

I don't think there are any complete or stable drivers for this card out yet, as I've tried the kernel drivers, the dkms drivers, and even the Realtek drivers. This is tragic.

Looks like I'm stuck with my old emu10k1 for the foreseeable future.

I actually hoped to use the on-board HDA and take out the sound blaster to make space for another card. I also like the way the hda does surround (actually upmixing) better than the sound blaster (relying on named channels in the audio stream).

---

