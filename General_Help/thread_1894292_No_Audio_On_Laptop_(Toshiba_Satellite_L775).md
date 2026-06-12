---
title: "No Audio On Laptop (Toshiba Satellite L775)"
date: 2011-12-12
forum: General Help
---

### Post by Spice Girls on 2011-12-12
I'm using Ubuntu 11.04 on a Toshiba Satellite L775

I was trying to install Realtek HD Audio Manager via the download from realteks site (the one listed under Unix (Linux), however, I learned that all it was, was just audio drivers.

After installing it. My sound is gone, I believe I have no sound driver now. When I go into the audio settings, there is nothing listed under hardware configuration and Output, it just says "Dummy Output Stereo".

Is there a way to install the default sound driver without having to reinstall to OS?

---

### Post by editheraven on 2011-12-12
Post the output of 
```

dpkg -l | grep alsa

```

---

### Post by Spice Girls on 2011-12-12
Here it is.

> ii  bluez-alsa                            4.91-0ubuntu1                              Bluetooth ALSA support
ii  gstreamer0.10-alsa                    0.10.32-1ubuntu5                           GStreamer plugin for ALSA
ii  libsnack2-alsa                        2.2.10-dfsg1-9                             Sound extension to Tcl/Tk and Python/Tkinter - Tcl/Tk library


---

### Post by editheraven on 2011-12-12
try

```

sudo killall pulseaudio
sudo apt-get install alsa-base
sudo alsa force-reload
*speaker-test*

```

---

### Post by Spice Girls on 2011-12-12
> **editheraven said:**
> try

```

sudo killall pulseaudio
sudo apt-get install alsa-base
sudo alsa force-reload
*speaker-test*

```

Nope, still nothing.

---

### Post by editheraven on 2011-12-12
Hmm.....try

```

sudo apt-get install alsa-utils
alsamixer
```

---

### Post by Spice Girls on 2011-12-12
> **editheraven said:**
> Hmm.....try

```

sudo apt-get install alsa-utils
alsamixer
```

Nope. When I see code on mutiple lines, like you have alsamixer on another line, do you paste the whole thing, or past the first line for, then the second, like to commends? I did both.

---

### Post by Spice Girls on 2011-12-15
Bump.

---

