---
title: "Soundblaster X-Fi Xtreme Audio Problems"
date: 2012-02-11
forum: General Help
---

### Post by shoot2kill on 2012-02-11
Hi, I am having trouble getting my Soundblaster X-Fi Xtreme Audio sound card working in Ubuntu.

When I first installed it, it kept stuttering and stopping. After following a few different "fixes" and forum posts, I managed to stop it from stuttering.

I then proceeded to connect my PC up to a 5.1 speaker system. When I went in to the settings to change the device from 2.0 to 5.1, I checked the 'Test Sound' button, and the test sound only plays out of the rear two speakers, and the centre speaker.

I have seen many forum posts and blogs saying that ALSA doesn't support this card, but most of them were old posts, and I can play it in 2.0 setup. (although it only plays through the centre speaker when I do that)

Does anyone have any ideas on getting it working please?

I am currently in the process of downloading and installing Ubuntu 11.04 (Natty) on the system, as I read a few posts where people say there card stopped working when they updated to Oneiric.

Any help would be very much appreciated.

Thanks

---

### Post by shoot2kill on 2012-02-12
Bump?!

---

### Post by shoot2kill on 2012-02-14
Fixed by adding
```

options snd-hda-intel model=5stack

```
to the end of /etc/modprobe.d/alsa-base.conf

---

### Post by Trent T on 2012-02-24
Thanks shoot2kill!

Your Soundblaster X-FI Xtreme fix also fixed the problem with my 
old Soundblaster " SBLive! EMU10K1 " board (which also stopped working after my upgrade to Ubuntu 11.04)

---

