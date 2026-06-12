---
title: "Audio Stutters"
date: 2012-07-29
forum: General Help
---

### Post by ChadCurtiss on 2012-07-29
I am running Ubuntu 12.04. I have an ASrock motherboard with built in audio. When I listen to audio of ANY kind it stutters and makes audio clicky noises like when you plug in speakers and they click as you plug them in. I am new to Linux so I am not sure if there was some sort of driver that I was supposed to install that I did not? But if I am going to use this I really need my audio to work properly. Thanks -Chad

---

### Post by jonnyboysmithy on 2012-07-29
Do you know the specific model of audio card? I suggest you google something like "how to find what audio card you have linux ubuntu" 
Perhaps have a read on: [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by ChadCurtiss on 2012-07-30
Well I did a little bit of testing and found that if I plug it into my front panel audio port instead of the main motherboard audio then it works fine. This is weird because in windows my front panel audio goes in and out constantly as if there is a short or something... which is what I always assumed. Not sure why now.

---

### Post by GreatDanton on 2012-07-30
> **jonnyboysmithy said:**
> Do you know the specific model of audio card? I suggest you google something like "how to find what audio card you have linux ubuntu" 


In terminal type:
```
lspci
```

and you will be able to found out which Audio card you have.

Regards.

---

### Post by coverturtle on 2012-07-30
Chad, 
Try installing a quality third-party audio card like one from turtle beach (do a little research) and see if that has different or no problems.

I´m assuming you have installed the latest BIOS version, are keeping 12.04 updated, and you are using the software provided by the ubuntu developers and the audio drivers are open source.  

It´s possible that the extension from the motherboard to the front panel may be acting as an antenna and picking up radio pulses from the motherboard - so . . .
If you know how to solder, you can try changing the wires to the front panel.  Replace with shielded audio cable or even shielded twisted pairs from a disassembled length of cat6 ethernet cable (preferably from bulk because patch cables are usually cheaper cable.) 

It may not help, though.  It´s probably easier to get and extension for the headphones and fasten the jack near the front panel with a piece of  duct 
tape. :grin:

If your parents live in MO, we may have met.
coverturtle

---

