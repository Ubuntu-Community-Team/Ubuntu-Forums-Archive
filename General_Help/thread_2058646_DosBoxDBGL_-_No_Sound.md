---
title: "DosBox/DBGL - No Sound"
date: 2012-09-16
forum: General Help
---

### Post by Shadius on 2012-09-16
Hey everybody! :)

I'm using DBGL to play Dune, but there's no sound. I've checked that I have the packages that the DBGL site says to have, but I'm still not getting any sound. Can someone help me here?

---

### Post by cwsnyder on 2012-09-16
Did you choose the Soundblaster driver when you installed Dune?

---

### Post by Shadius on 2012-09-16
> **cwsnyder said:**
> Did you choose the Soundblaster driver when you installed Dune?

I don't think so. I don't think I have a Soundblaster card though?

---

### Post by cwsnyder on 2012-09-16
For your reference, DOSBox maps your Linux sound card to a Soundblaster 16 and maps your Video card driver to EGA, VGA or other modes which will be supported in DOS games, but maybe not by your video card.

In DOS games, you must tell it you have a sound card and what type it is (maybe even giving the proper interrupt and port address) to get sound to work.

---

### Post by Shadius on 2012-09-16
> **cwsnyder said:**
> For your reference, DOSBox maps your Linux sound card to a Soundblaster 16 and maps your Video card driver to EGA, VGA or other modes which will be supported in DOS games, but maybe not by your video card.

In DOS games, you must tell it you have a sound card and what type it is (maybe even giving the proper interrupt and port address) to get sound to work.

Oh okay. When I set up DBGL, I just left everything as the default. Video is fine, but no sound. I tried to adjust the sound from within the game, but I doesn't let me. The options for sound are disabled. I can provide a screenshot of the "Audio" tab of DBGL if that'll help you help me better since I have no idea what I'm doing.

---

### Post by cwsnyder on 2012-09-16
If you left DBGL as default, that is probably OK.  Your sound options in Dune probably are disabled because you didn't enable them when you installed Dune.

---

### Post by Shadius on 2012-09-16
> **cwsnyder said:**
> If you left DBGL as default, that is probably OK.  Your sound options in Dune probably are disabled because you didn't enable them when you installed Dune.

Alright, so how do I go about doing that now?

---

### Post by Shadius on 2012-09-16
Here's a screenshot of my DBGL "Audio" tab.

---

### Post by cwsnyder on 2012-09-16
I don't really know Dune, so the best I could direct you is to re-install Dune and watch your options.

---

### Post by kostkon on 2012-09-16
I think the "Run Setup" button allows you to run the setup.exe file of a game, if it has one, not sure though. Otherwise, in plain dosbox, not dbgl, just mount the game's folder and then run the setup.exe file. Dune2 comes with such a setup utility.

---

### Post by Shadius on 2012-09-16
I've tried running the setup. Didn't work. It's not Dune 2, it's Dune. I'm going to try redoing it.

---

