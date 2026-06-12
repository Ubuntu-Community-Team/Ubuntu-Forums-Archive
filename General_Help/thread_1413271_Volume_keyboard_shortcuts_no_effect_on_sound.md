---
title: "Volume keyboard shortcuts no effect on sound"
date: 2010-02-22
forum: General Help
---

### Post by unxposed on 2010-02-22
I had problems getting sound working on a new install of 9.10, and eventually got it working by going to gnome alsa mixer and increasing Master F which was near 0%.

Sound works now, but the fn+F10/F11 (volume up/down) keyboard shortcuts which show volume increasing and decreasing in sound preferences have no effect on the volume.

How can I get these shortcuts working again?

Thanks!

---

### Post by unxposed on 2010-02-22
Okay so this is a larger problem that I thought.

Any file/radio I play through rhythmbox produces no sound, I'm sure sound is not working in other apps as well. If I go to pulse audio I can see there should be output from rhythmbox but there isn't.

Basically sound wan't working at all after install and I followed this process [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) installed the latest version of alsa 1.0.22, and then opened alsa mixer and increased the masterf pcm, front sliders - I thought I had solved the problem as sound in spotify/ google chrome came on.

However:
> Rhythmbox doesn't produce sound
> Keybinding shortcuts don't increase/decrease sound
> Sound preferences - nothing under hardware or input - only thing under output is "simultaneous output (stereo)"
> PulseAudio volume control nothing under configuration

I've looked through posts on this all day, not sure what to do?

Thanks

---

