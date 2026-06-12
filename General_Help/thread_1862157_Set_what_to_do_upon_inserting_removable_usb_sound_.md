---
title: "Set what to do upon inserting removable usb sound card for wireless headset"
date: 2011-10-16
forum: General Help
---

### Post by Colin Keenan on 2011-10-16
Ubuntu 11.10

I have a wireless headset that I use for google talk/voice phone calls. At first, the only way I could see to use it is to follow this very lengthy process each time, far too lengthy to actually answer a call:

1) insert usb sound card dongle for the wireless headset.
2) Turn on the headset.
3) Open Sound Settings.
4) Click the Input tab.
5) Select the newly inserted sound card.
6) Click the Output tab.
7) Select the newly inserted sound card.
8) Try to answer the call, but they already hung up.

I have shortened this process by figuring out how to put steps 3-7 into a simple 2-command script as follows:

pacmd "set-default-sink alsa_output.usb-Plantronics_Wireless_Audio_Plantronics_Wireless_Audio-00-Audio.analog-stereo"

pacmd "set-default-source alsa_input.usb-Plantronics_Wireless_Audio_Plantronics_Wireless_Audio-00-Audio.analog-mono"

I put the script called "headset.sh" in /usr/local/bin and put a .desktop file for it in /usr/share/applications and set both files to executable. I couldn't figure out how to get the .desktop file to show up in the Unity launcher, so I put a link to the .desktop file in my home folder and set the permissions to have me as the owner instead of root. Now my list of steps to use the headset is much shorter:

1) insert usb sound card dongle for the wireless headset.
2) Turn on the headset.
3) Open home folder from Unity Launcher.
4) Click on the link to the headset.desktop file.

**So my question is this: is there anyway to eliminate the last 2 steps? I want the headset.desktop or the headset.sh file to be called automatically upon inserting the removable usb sound card for my wireless headset**. This would be very similar to what can already be done upon inserting removable media except the usb sound card for my wireless headset is not "media".

If I should post this in another forum, please tell me which one, because I didn't really see any relevant ones. All the hardware works fine so the multimedia or hardware forums don't seem appropriate. This is more of a programming issue I guess.

---

### Post by Colin Keenan on 2011-10-16
I just learned how to add any .desktop file to the launcher in Unity:[B] *drag the .desktop file to the launcher! *
[/B]
How easy is that?:D I've been using Unity for over half a year and have been struggling with that this whole time.

So now it's really not that bad for me to use the headset. There's just 3 steps:

1) Plug in usb dongle for the headset
2) Turn on headset
3) Click headset.desktop in Unity launcher panel

It still would be great if headset.desktop could run automatically whenever I plug in the usb sound card dongle for my headset.

Any ideas on how to accomplish that?

---

