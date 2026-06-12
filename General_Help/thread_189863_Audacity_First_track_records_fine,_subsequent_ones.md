---
title: "Audacity: First track records fine, subsequent ones sound weird"
date: 2006-06-05
forum: General Help
---

### Post by OneSeventeen on 2006-06-05
I'm trying to start a podcast, and when I record my first track into Audacity from my microphone it sounds great (better than on my windows PC), but then when I stop, then start recording again, all of the new tracks it records sound like it shifts the pitch down quite a bit.  It would be a cool effect if it were intentional, but its not, so any tips on avoiding this would be awsome!

(and yes, this is new with Ubuntu 6.06... with previous versions it wouldn't even let me record, so this is a huge step up!)

---

### Post by sharperguy on 2006-06-05
I have the same

I also had it on windows though.

---

### Post by cleentrax on 2006-06-05
1. What soundcard are you using? 
2. Is it Linux compatible? 
3. Is it full-duplex? (able to record and play back simultaneously)
4. What are its sample rate options? 
5. Are you using compatible sample rate in audacity?

---

### Post by scratched on 2006-06-05
I had this same exact problem yesterday and I figured out a solution by accident. Let me know if this works.

In Audacity, click **Edit > Preferences** and make sure you are on the Audio I/O tab in the dialogue that comes up(that's where it goes by default for me).

Click the box next to "Play other tracks while recording new one." Also, I'm not sure if this is necessary, but I also have the Software Playthrough box clicked.

I'm not sure why, but this fixed my problem. Give it a shot and let me know if it fixed your problem.

---

### Post by OneSeventeen on 2006-06-06
Thanks scratched, I'll try that out tonight.

cleentrax: to show my newbieshness, how do I find those details about my soundcard?
(it is built-in sound, unfortunately, but I'm not closed to purchasing a PCI sound card)

---

### Post by cleentrax on 2006-06-06
117,

You could try to look up some info based on the model of motherboard in your computer. Once you know that, you should be able to find out whether the onboard audio is full-duplex.

Basic PCI sound cards, such as a Soundblaster Audigy, are full-duplex, though you may have to change some settings.

None of the four audio cards in my recording studio work properly with Linux, so sadly most of my audio  expertise is with Windows.

I have tried editing in Audacity with my Inspiron 8600 and the onboard audio, and it was a frustrating experience. I find Audacity to be ugly and unintuitive. It took a lot of steps to duplicate things I can do easily in Wavelab or Sound Forge. I also had some difficulties with a screeching sound card any time I made changes in Audacity's settings, which required reloading Gnome. But that may be a driver issue, and not the fault of Audacity.

Are you using Audacity with ALSA or without?

---

