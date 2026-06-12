---
title: "Sound problems"
date: 2010-08-21
forum: General Help
---

### Post by DeMus on 2010-08-21
Hi,
I am still having problems with my sound. I had this with many distro's so I start to believe either there is something wrong with my hardware, or I need something which no distro has got.
The problem is:
sometimes I have no sound. This is either from the start, or like now, after having done several things already. I did listen to music (Banshee), I did watch a movie (VLC) and now I wanted to play a game and I have no sound.
Whenever that happens, when I click on Sound Preferences I get the window like in the attachment. The window is much too long, it stretches way beyond my monitor. I can not do anything in that window since the buttons are not visible. When I maximize it and I click on it, I see the bottom part. Clicking a button there shows me the top part again. In other words I can not use it.
Who can help me with it?
I use the 64-bit version of Lucid Ultimate Edition
My sound "card" is:
```
lspci |grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by DeMus on 2010-08-22
No one who can help me? I sure could use some help.

---

### Post by smarmytime on 2010-08-22
So the sound, it comes and goes? Or do you do something that brings it back? You weren't entirely clear with what happened after you maximized sound preferences. Do you raise the volume? It looks like it's very low.

What happens if you just click on the volume icon? When I do it, it shows me a very simple slider, which you pull to the right to raise the volume, and to the left to lower it. It also has two other options - one, to mute/unmute, and two, to bring up the full Sound Preferences dialog box.

Does your volume always disappear in the same manner? Can you always hear your music and the sound from movies? Is it only the video game that's affected, or is it random? If there are any consistencies, that would help troubleshoot your problem.

---

### Post by DeMus on 2010-08-22
> **smarmytime said:**
> So the sound, it comes and goes? Or do you do something that brings it back? You weren't entirely clear with what happened after you maximized sound preferences. Do you raise the volume? It looks like it's very low.

What happens if you just click on the volume icon? When I do it, it shows me a very simple slider, which you pull to the right to raise the volume, and to the left to lower it. It also has two other options - one, to mute/unmute, and two, to bring up the full Sound Preferences dialog box.

Does your volume always disappear in the same manner? Can you always hear your music and the sound from movies? Is it only the video game that's affected, or is it random? If there are any consistencies, that would help troubleshoot your problem.

Thanks for your answer.
If there is a consistency, I did not find it. Sometimes after boot when I look at the Sound Preference Window it is large already, meaning I have to reboot again because I have no sound.
Other times it is okay after boot so I can hear sound from whatever program I want to use. Then after closing it down and starting another program it doesn't work anymore. Looking at the Sound Preferences shows me a large screen, like on the attachment, and I can reboot again.
No, it's not a matter of the volume. In the early morning I set it so low so I don't wake up my wife and/or daughter.
When I click on the volume icon I also get the slider and the buttons for Mute and Preferences. That works. To raise or lower the volume I use the extra keys on my keyboard, not the slider.
I had this with other distros as well. With Fedora and Mandriva I had even more problems with sound, that's why I returned to Ubuntu, but also with this edition it doesn't always function as it should. Some days I have no problems at all, other days I can just forget using sound at all.

---

### Post by DeMus on 2010-08-22
I am deeply ashamed. I have just found the solution to my sound problem AGAIN. I have had this before and also then found the solution. Now with a new installation things went wrong again.
This whole thing is caused by the Chrome Sounds add-on in Google Chrome. When I disable this add-on the problems are gone. I will even un-install it to make sure the problems don't come back again.
Hope I have helped others as well who are experiencing strange sound behavior and have the sounds add-on enabled.

---

### Post by Dinahalye on 2010-08-22
i learn more at this forum:popcorn:

---

