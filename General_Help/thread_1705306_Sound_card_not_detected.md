---
title: "Sound card not detected"
date: 2011-03-12
forum: General Help
---

### Post by stuart221 on 2011-03-12
I'm Running ubuntu 10.10 with kubuntu 10.10 as well so I have no problems with ubuntu but when I login with kuntuntu I have sound but I get massage that kunbutu can't detect my  sound card any more would you like it to forget it.Plus I can't change volume no volume icon on task bar.

---

### Post by ankspo71 on 2011-03-13
Hi,
This should help get you started: 
This Info is gathered from: [http://pulseaudio.org/wiki/KDE](http://pulseaudio.org/wiki/KDE)

Go to System Settings > Multimedia > Phonon > Device Preference (tab).
Do you see your sound card listed for Audio Output? 
Or do you see "PulseAudio Sound Server" listed there?
Or is it blank or have "Dummy Output" listed?

If you only see "PulseAudio Sound Server" or "Dummy Output" listed there, then it is possible that pulseaudio is either crashing or failing to start in KDE.

Close your System Settings window (and discard changes if necessary).

Open your terminal and paste the following command:
```
start-pulseaudio-kde
```

If you run that command and it gives the error: "Failure: Module initalization failed", then it could mean that the kde pulseaudio module is already running... so try this:
```
killall pulseaudio
start-pulseaudio-kde
```

Now Go back to System Settings > Multimedia > Phonon > Device Preference (tab).
Do you see your sound card listed for Audio Output now?

If you have determined that this was the problem, then I recommend reinstalling pulseaudio and kubuntu-default-settings to see if it helps keep pulseaudio running. 

Here are some more troubleshooting links:
[http://pulseaudio.org/wiki/KDE](http://pulseaudio.org/wiki/KDE)
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[https://wiki.kubuntu.org/PulseAudio](https://wiki.kubuntu.org/PulseAudio)

---

