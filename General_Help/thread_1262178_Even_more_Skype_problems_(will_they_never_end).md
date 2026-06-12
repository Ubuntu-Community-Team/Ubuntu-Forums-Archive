---
title: "Even more Skype problems (will they never end)"
date: 2009-09-09
forum: General Help
---

### Post by frogbrains on 2009-09-09
Ok, so I just downloaded the new version of Skype, called somebody, and apparently all they hear is white noise.  Tested this out in the test call, and he was right.  Just a horrible noise.  I can't change the audio device in Skype because the only option is "PulseAudio server (local).  I am getting fed up with all these bloody Skype problems.  On the plus side, other stuff can now make noise at the same time as Skype (never could before).

---

### Post by P4man on 2009-09-09
can you record something in audio recorder or any other app?

Since the new skype (finally!) uses pulseaudio, you should configure your sound input in system > preferences > sound and/or gnome mixer. Try switching mic input (many cards have 2).

---

### Post by kostkon on 2009-09-09
Install the *PulseAudio Device Chooser* utility using Synaptic. It will allow you to send the audio from Skype to any device you want.

For more info check [here]("http://ubuntuforums.org/showthread.php?t=1130384") (the instructions apply even if you are using 8.10).

---

### Post by pevzi on 2009-09-10
I have the same problem. After some time talking in skype, the microphone sound turns into annoying white noise and it happens randomly. Also, the noise appears not only in skype, it appears absolutely everywhere (e.g. in System -> Properties -> Sound in Recording test it can be heard too) so it replace all the sound comes from microphone. Do you know how this problem can be solved? Maybe my computer's characteristics are too low (I'm using EeePC 1000H)?

---

### Post by P4man on 2009-09-10
> **pevzi said:**
> I have the same problem. After some time talking in skype, the microphone sound turns into annoying white noise and it happens randomly. Also, the noise appears not only in skype, it appears absolutely everywhere (e.g. in System -> Properties -> Sound in Recording test it can be heard too) so it replace all the sound comes from microphone. Do you know how this problem can be solved? Maybe my computer's characteristics are too low (I'm using EeePC 1000H)?

Have a look here:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/354620](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/354620)

Also make sure you have all updates installed, I believe some audio bugs where fixed for the EeePC recently.

---

### Post by pevzi on 2009-09-10
> **P4man said:**
> Have a look here:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/354620](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/354620)


As I could see, there is about sound shattering that is not stopping. But I am about white noise that starts suddenly and stopping some minutes later.

> **P4man said:**
> 
Also make sure you have all updates installed, I believe some audio bugs where fixed for the EeePC recently.

All updates are installed, there is nothing more to update.

---

### Post by pevzi on 2009-09-14
up  -_-

---

### Post by richardmalter on 2009-09-14
I have the problem that I cannot record sound (on skype), can anyone help me check what settings I should have? Thank you!

---

### Post by Benzaa on 2009-09-14
Check your Pulse audio volume control while making a call in skype.

You can select different audio streams for recording

---

### Post by xx58 on 2009-09-18
I can say next: Use Stable version SKYPE, not a BETA Version and this all your problems just will go a way.

---

