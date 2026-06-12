---
title: "HP 625 Notebook - No audio on 11.04 (natty)"
date: 2011-05-22
forum: General Help
---

### Post by mrplow887 on 2011-05-22
I had the joy to install Ubuntu 11.04 (natty) on an HP 625 notebook.
Install was clean and easy (with updates) but I can't get the sound to work.

Device is "HDA *ATI* SB" with internal speakers and headphone jack
Codec reported and used is IDT 92HD88B1.

I already searched these forums, launchpad bug tracker and google for solutions. I found various mailing lists, threads and bug reports dealing with this issue, but they were either very outdated (ubuntu 9.xx) or on other notebooks. 

alsa-driver package version is 1.0.24+dfsg-0ubuntu1 with *cat /proc/asound/version* reporting 1.0.23.

From the various threads concerning this notebook, users had the following problems:
1. No sound outpout at all (speakers, headphone jack) - this is my problem, too
2. Some sound output (only headphone jack)
3. microphone not working (but output seemed to work)

From users with ubuntu 10.04 the update from ALSA 1.0.22 to >=1.0.23 fixed the problem (some stating after upgrade to natty it fails again).
Problem with ALSA <1.0.23 was that certain HDA devices were not identified correctly.
Comparing their logs to mine, on my system the devices are identified correctly.
[B]
So what did I try to fix it?[/B]
1. Recompiled the alsa driver and modules, because the driver reported by the system is not the latest one
Outcome: Devices aren't detected anymore
After further reading of forum posts with this solution, I may have forgotten to sepcify some compile time options. Maybe this will work on another try.

2. Installed 10.04 and upgraded ALSA to >=1.0.23
Outcome: Still no output at all

3. Tried various lines and configs (including option snd-hda-intel model=... or enable_msi=1 in /etc/modprobe.d/alsa-base.conf)
Outcome: No change, still no sound at all

4. Checked alsamixer if devices were muted
Outcome: Everything enabled and at 100%

5. Upgraded packages with natty-backports
Outcome: No change, still no sound at all

**What didn't I do?**
1. There's an HDMI jack which is supposed to output audio, too. I didn't have a HDMI capable device at hand so I wasn't able to test audio output via HDMI.

Anyone else having this problem or does anyone know how to get the precious audio to work? Spent the weekend on this :D

I refuse to fall back to Windows.

PS: Since I'm a new member here: Hello and maybe I can help someone else here, too :)

EDIT(s): fixed Device name

---

