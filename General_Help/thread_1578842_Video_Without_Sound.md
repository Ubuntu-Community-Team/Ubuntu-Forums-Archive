---
title: "Video Without Sound"
date: 2010-09-21
forum: General Help
---

### Post by magiceffects on 2010-09-21
I have a problem with my Video recording without any sound. I have looked into the fixes of the 64bit MMPEG upgrades and gone through what steps I can find to fix the problem, although even after going through the re-compile in konsole, as well as then removing it and trying again using K Package Manager, I still have no Audio with my Video when recording in Cheese.

Cheese records the video in ogv format, and I have attempted to convert the ogv file to avi format using VLC. I am able to watch the video in both VLC and Dragon Player... but no sound, just video. I have used Cheese to record video's using Ubuntu 8.10 onwards, but my current Kubuntu 10.04.01 (and when I had 10.04) has no sound in the recordings. I have not changed microphone, and I have checked all my connections. I can hear voice in the speakers through the microphone.

I am using on board sound, which I have no other issues with. The error message I get tells me that my MMPEG install lacks the AAC Audio Codec.

Any suggestions? I am a bit newbie so please let me know if there is more information I need to add.

Thanks

---

### Post by robsoles on 2010-09-21
Pretty sure Cheese doesn't do sound.

Checkout VLC Media Player, it's in the repository so best gotten from there. (Pretty sure it offers functionality to record video with sound with good selection of devices where available.)

---

### Post by magiceffects on 2010-09-22
Cheese does record with sound, I have already mentioned it was working in previous distributions of Ubuntu/Kubuntu...

I already use VLC Media Player, which is NOT a webcam recording application, as is Cheese, and the fact I have been using VLC is ALSO mentioned above. How was this reply meant to help?

---

### Post by robsoles on 2010-09-22
On my system(s) Cheese program doesn't mention sound in any way, shape or form, and in the manual for cheese I didn't find any mention of sound in the parts I checked for a mention so I dismissed the fact that you say it worked before so as to post something I felt should help.

VLC can record your video with audio from your webcam & microphone - checkout 'Media'->'Streaming'

---

### Post by magiceffects on 2010-09-22
I understand, sorry if my reply seemed blunt. I have been using Cheese for the last 3 or 4 distributions without any problems and it was previously recording video with sound also...

I was unaware that VLC allowed you to record video using your webcam, although I intend to investigate this and see if its any better.

I do however feel that it would not matter what application I use to record, as the AAC Audio Codec is failing regardless. I have tried 3 of the codec fixes I can find with no result.

---

### Post by robsoles on 2010-09-22
VLC is a monster of features.

Have you used 'aac' as a filter in the Synaptic Package Manager?

---

### Post by magiceffects on 2010-09-24
I give up. I've spent 11 days straight trying to fix this and gone through 4 different forum threads that sound like they could solve the problem. I think 10.04 really put Ubuntu down. This is one of many faults i've noticed so far and I think its time to go back to Windows.

Good luck anyone else who has this problem.

---

