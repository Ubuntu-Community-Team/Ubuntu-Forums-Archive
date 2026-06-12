---
title: "keyboard synth for ubuntu?"
date: 2009-10-17
forum: General Help
---

### Post by austinmathis on 2009-10-17
im looking for a synthesiser program for my computer one where i can just press keys on my computer and it make noise.i dont want just a keyboard i want it to have effects also is there any program like this or am i just imagining there is

---

### Post by StuartN on 2009-10-17
> **austinmathis said:**
> im looking for a synthesiser program for my computer one where i can just press keys on my computer and it make noise.i dont want just a keyboard i want it to have effects also is there any program like this or am i just imagining there is

Linux has a really nice, modular approach to this. Install Virtual Midi Keyboard (vkeybd) and the ALSA Connection Utility (aconnectgui). You can then open Virtual Keyboard and the Connection Utility, click on the output of Virtual Keyboard and drag it onto the input of Timidity (which is already installed).

Clicking the keyboard image should make sound. The computer keys are also mapped to notes.

When you want more sounds you can install any other ALSA synth and route the Virtual Keyboard into it. You can also add audio processors and send output from synth-to-synth.

---

### Post by austinmathis on 2009-10-17
hmm thanks alot umm ill post back if i have any prolblems with doing this

---

### Post by austinmathis on 2009-10-17
i downloaded alsa nad the keyboard but i have no idea what to do next im sry im new to all this

---

### Post by StuartN on 2009-10-17
> **austinmathis said:**
> i downloaded alsa nad the keyboard but i have no idea what to do next im sry im new to all this

If you select Applications->Sound and Video->Virtual Midi Keyboard then it should open a window with a picture of a keyboard on it. If you select Applications->Sound and Video->Aconnectgui you should have a window titled "ALSA Sequencer" (although it is not a sequencer).

Click the two plugs (connect) icon. Move the mouse cursor over the right-pointing arrow (output) of the Virtual Keyboard, click and hold, move the mouse cursor over the left-pointing arrow (input) of Timidity port 0 and let go. There should be line connecting the keyboard to the synth, and clicking keys should make sound. So should keyboard key-presses.

---

### Post by austinmathis on 2009-10-17
is there any way i can add more effects like a synthesizer?

---

### Post by StuartN on 2009-10-17
> **austinmathis said:**
> is there any way i can add more effects like a synthesizer?

Yes, Timidity is some fixed standard sounds. You could try ams, bristol (neither worked for me), fluidsynth, hydrogen, spiral and zynaddsubfx from the repositories. You could search for "Linux synth" to find more.

And then you will want Jack audio transport, because that way you can do real-time performance with audio effects, recording, etc.

---

### Post by austinmathis on 2009-10-18
hey thanks alot

---

### Post by austinmathis on 2009-10-18
im sory but how would i go about accessing these effects

---

### Post by StuartN on 2009-10-19
> **austinmathis said:**
> im sory but how would i go about accessing these effects

The easiest way is to use the ALSA Connection Utility. If you have ZynAddSubFX installed then start it up, start up the Virtual Keyboard, start Aconnectgui and link the keyboard output into the synth. Unlike Timidity, which is always running, other synths have to be started up.

---

