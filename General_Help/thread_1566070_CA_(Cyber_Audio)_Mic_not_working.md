---
title: "CA (Cyber Audio) Mic not working"
date: 2010-09-01
forum: General Help
---

### Post by gypsumwolf on 2010-09-01
This is in Ubuntu 10.04. (It is actually Cyber Acoustics, not "Audio" as in my title)

I have checked settings in *PulseAudio Volume Control* and I tried different things like moving the volume above 100% with the *PulseAudio Device Chooser*.

My mic is this almost exactly the same as this one: [http://www.officedepot.com/a/products/453750/Cyber-Acoustics-CVL-1124R-MonitorLapel-Microphone/]("http://www.officedepot.com/a/products/453750/Cyber-Acoustics-CVL-1124R-MonitorLapel-Microphone/")

**The actual model of mine is:** CVL-1124
**The model of the link I gave:** CVL-1124R

**My Soundcard is:** nVidia Corporation MCP61 High Definition Audio (rev a2)
**Subsystem:** Biostar Microtech Int'l Corp Device 8108

---

### Post by gypsumwolf on 2010-09-02
**Solved!:**

**1)** Installed "*_Xubuntu 10.04_*" instead of "*_Ubuntu 10.04_*".

**2)** Installed "*_Sound Recorder_*" for testing purposes.

**3)** Clicked on speaker icon next to the clock in upper XFCE panel to bring up "*_Mixer_*", with Sound Card: "*_VIA VT1708 8-Ch (OSS Mixer)_*" selected, click "*_Select Controls..._*" and check "*_In-gain_*".

**4)** I turned the *_In-gain_* all the way up, tested it with "*_Sound Recorder_*"and it works perfectly!

---

