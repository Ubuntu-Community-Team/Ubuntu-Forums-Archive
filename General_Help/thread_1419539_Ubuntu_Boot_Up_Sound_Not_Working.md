---
title: "Ubuntu Boot Up Sound Not Working"
date: 2010-03-02
forum: General Help
---

### Post by emagine on 2010-03-02
Hello everyone,

I recently noticed that when I boot up ubuntu it no longer plays the cool startup music.  I think it may have something to do with me removing these packages in synaptic package manager because they were interferring with my sound in total annihilation for spring. Most of the packages below were reinstalled because my sound icon disappeared and I had to reinstall them.  But are any one of these packages responsible for the ubuntu boot up sound?

gstreamer0.10-pulseaudio
libcanberra-pulse
pulseaudio
pulseaudio-esound-compat
pulseaudio-module-bluetooth
pulseaudio-module-gconf
pulseaudio-module-udev
pulseaudio-module-x11
pulseaudio-utils
ubuntu-desktop

Thank you.

---

### Post by dcstar on 2010-03-02
> **emagine said:**
> Hello everyone,

I recently noticed that when I boot up ubuntu it no longer plays the cool startup music.  I think it may have something to do with me removing these packages in synaptic package manager because they were interferring with my sound in total annihilation for spring. Most of the packages below were reinstalled because my sound icon disappeared and I had to reinstall them.  But are any one of these packages responsible for the ubuntu boot up sound?

gstreamer0.10-pulseaudio
libcanberra-pulse
pulseaudio
pulseaudio-esound-compat
pulseaudio-module-bluetooth
pulseaudio-module-gconf
pulseaudio-module-udev
pulseaudio-module-x11
pulseaudio-utils
ubuntu-desktop

Thank you.

 think that the libcanberra subsystem is used for the boot-up sounds (they are different from the login sounds).

Also the x11 package is probably important.

---

### Post by emagine on 2010-03-03
> **dcstar said:**
> think that the libcanberra subsystem is used for the boot-up sounds (they are different from the login sounds).

Also the x11 package is probably important.
I  Installed both of them and my boot up sound still isn't working.  Could it be a different one?

---

### Post by emagine on 2010-03-03
I figured out the problem.  It did not have to do with the packages.  All I had to do was right click the sound icon in the top right and go to sound preferences.  From there, under sound effects I unmuted the alert volume and confirmed that ubuntu was the default sound theme.

---

