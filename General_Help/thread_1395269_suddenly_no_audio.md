---
title: "suddenly no audio"
date: 2010-01-31
forum: General Help
---

### Post by typos1 on 2010-01-31
Sound suddenly gone, tried messing around with settings for a couple of hours, makes no difference, cannot get any sound at all. Since upgrading to Karmic have lost the ability to test sound settings. Dont know what to do. Not expecting any replies, or help, as usual, with ubuntu your on your own and if you cant figure it out then you re stuck

---

### Post by typos1 on 2010-02-01
Anyone?

---

### Post by TheNessus on 2010-02-01
> **typos1 said:**
> Sound suddenly gone, tried messing around with settings for a couple of hours, makes no difference, cannot get any sound at all. Since upgrading to Karmic have lost the ability to test sound settings. Dont know what to do. Not expecting any replies, or help, as usual, with ubuntu your on your own and if you cant figure it out then you re stuck

machine? card? make? happened after upgrade? was it upgrade or clean install?

---

### Post by typos1 on 2010-02-01
Acer Aspire T-180 AMD 64 X2 3800+. Onboard sound. Upgrade, not clean install. The upgrade sorted all probs Jaunty had with playing Flash stuff (only played some movies, never iplayer and no sound in Flash at all). After upgrade had different sound preferences window with no mention of "ALSA" or "OSS" but all Flash stuff played and WITH sound.

In Jaunty there were loads of bugs if I changed visual effects to normal or enhanced (including loss of minmise, expand and close controls in top right of windows). Recently had to fit a new BIOS chip as the old one failed (commonn Acer prob) and the new one recognised the extra 1GB of RaM I brought 2 years ago (finally!), so thought I d try and try enhanced visual effects again-same prob, no window controls and very buggy, so changed back-eventually.

Afterwards re booted and got start up music but no sound in anything. Cant see how visual effects could effect sound-must be coincedence...? Restarted several times since and no startup sound either.

Tried uninstalling ALSA mixer and installing PulseAudio manager and a few related apps-made no difference. Dont know what to do.

---

### Post by jimbob on 2010-02-01
Open a terminal window.  Type in alsamixer.  Make sure everything is not muted. Are all the settings  (particularly master) up in the red?

---

### Post by typos1 on 2010-02-01
Yep, everything in red. The settings in gnome volume control are all at high, still no sound

---

### Post by jimbob on 2010-02-01
Weird.  Don't know what to suggest. Do you have external speakers connected or headphones?  Are they both silent?

If you have a dual boot does the other OS operate normally?

---

### Post by typos1 on 2010-02-01
External speakers connected via usb. Under sound preferences/hardware is "internal audio stereo output and "usb audio device". After my fiddling "usb audio device" no longer appears. It was still there when sound first stopped, though. Tried unplugging and re connecting the audio device-nothing. It has an LED on it to show its working-the LED is lit...Got XP-I ll try rebooting using that. God I hate it-it takes soo long to boot up!

---

