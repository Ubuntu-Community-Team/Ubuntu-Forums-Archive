---
title: "not the usual Skype audio question..."
date: 2009-10-24
forum: General Help
---

### Post by akahige on 2009-10-24
Skip down a few posts to see the workaround. (Initial post left for context.)



I decided I'd try the new Skype beta (2.1.0.47) and am sorting out the differences between it and v2. I was running pulseaudio before, and unlike some people, I've had good luck with it.

The new version of Skype -- being PA-based -- is giving me fits in one particular aspect. With v2, the sound notifications played through the desktop speakers, while chat audio was redirected to the headset. In 2.1, I only seem to be able to play sounds on one device or the other. So I can either play the notifications in my headset, or the chat conversation over the speakers.

I don't know if this is a bug, or a limitation, or just something I'm doing wrong.

Anybody got any thoughts...?



Running:
Skype 2.1.0.47
Karmic AMD64
pulseaudio 0.9.19

---

### Post by P4man on 2009-10-24
Not sure this will help, but Using the PA device chooser > preferences you can enable simultaneous output on different sound devices. Then you can configure that simultaneous output as default output for a given app or in general  in pulse audio volume control. Both tools need to be installed though.

---

### Post by akahige on 2009-10-24
I've got the PA controls installed, but if I'm understanding your suggestion correctly, I think it's the exact opposite of what I'm trying to achieve. I don't want the sound alerts in both places. I only want them on the speakers and NOT in the headset.

---

### Post by akahige on 2009-10-24
After some hours of digging, I ran across a suggestion that didn't quite work, but still allowed me to achieve what I was after with a hint of modification. Sharing it here so anyone else who wonders the same thing will have a workaround.


Since there is no differentiation in Skype between sound devices when using Pulse Audio, the simple trick is that you can use a script to call some other applet/application which you can then isolate in the PA Volume Control manager.

Because I have ALSA installed, I also have alsa-utils which comes with a CLI audio player: "aplay". (There may be any number of other suitable apps.)

To convert the Skype behavior:
1) Open the Pulse Audio Volume Control applet and make sure that the **Playback** tab is selected; then open **Skype > Options > Notifications > Advanced View**.

2) Check "Execute the following script" and type the name of your preferred player, the path to the Skype sounds -- /usr/share/skype/sounds -- and the name of the audio file which is specified a few lines above on the "Play Sound File" line.

I started with the first event -- Skype Login -- because it's a long sound effect.

The script line looks like this:
```
aplay /usr/share/skype/sounds/SkypeLogin.wav
```

3) Uncheck "Play Sound File".

4) Click "Test Event" and jump over to the Pulse Audio Volume Control applet. You should see aplay appear, and there should be enough time to select the stream switcher and change from your headset device to speaker output.

5) Once you've confirmed that it works, you can go through the list of Skype notifications and change every thing that plays a sound file to play using the external, isolated in PA audio player. (There aren't that many of them.)

---

### Post by Neil Woolford on 2010-01-05
A good workaround, but it can be enhanced to use more of the features of PulseAudio.

If instead of using aplay /thepath/to/skypesound/CallRingIn.wav, try using
```
paplay   --property=media.role=event /usr/share/skype/sounds/CallRingingIn.wav
```

paplay is pulse's own audio player, and communicates with the rest of PulseAudio;  in this case the --property=media.role=event parameter means the sound follows the same routing as other system alerts such as window and button sounds.

This means that the volume of the alert can be controlled from the Sound Effects tab of Sound Preferences, and should automatically route to speakers by default on a normal setup, rather than having to re-route effects from the applications tab in stage four of the workaround.

Hope this helps...

---

### Post by akahige on 2010-01-06
Thanks, Neil. This is very cool. I appreciate you passing it along. I look forward to testing it out.

One "advantage" of the aplay implementation is that I can set the volume to something completely independent of the system alerts (for my preference, much lower).

Cheers!

---

