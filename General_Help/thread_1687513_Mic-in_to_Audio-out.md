---
title: "Mic-in to Audio-out"
date: 2011-02-14
forum: General Help
---

### Post by micha8l on 2011-02-14
Hey I think I need someone who knows a fair bit about audio on Ubuntu to help, please.

I'm trying to listen to my Xbox 360 Sound via a special cable which connects my Xbox to my PC. This is the cable: [http://www.amazon.com/Xbox-360-VGA-HD-AV-Cable/dp/B000B6MLTG](http://www.amazon.com/Xbox-360-VGA-HD-AV-Cable/dp/B000B6MLTG) (what it doesn't show is the connector that the red and white cables plug into; it's like a small connector with input for the red and white that output to a male audio jack). So I stick the jack into my PC's Mic Slot ( pink ) and I stick my headphone's into my PC's headphone slot and I hear nothing. But when I stick the headphone's in my PC's second mic slot ( at the front-side of my computer) I hear the Xbox sound through one headphone speaker..... I don't know, I've tried all types of variations and I just can't get it working, can you guys help?

Kind Regards,
Mike

---

### Post by micha8l on 2011-02-14
Bump

---

### Post by micha8l on 2011-02-14
Bump

---

### Post by sydbat on 2011-02-14
Have you tried to plug it into the "Line-In" input on your sound card? Then, have you chosen the input and output in Sound Preferences?

---

### Post by micha8l on 2011-02-14
I got this working by going to terminal and typing 'alsamixer' use the arrow keys to navigate to <Mic Sele> and select your mic slot. Then goto <Line Jack> and make sure it's set to on, use the M key to change setting. Other than that just make sure everything that should be unmuted and that volume is turned up! :)

---

