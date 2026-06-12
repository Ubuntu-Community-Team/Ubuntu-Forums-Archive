---
title: "Who told my keyboard what to do?"
date: 2009-07-15
forum: General Help
---

### Post by gwm on 2009-07-15
I have a new Logitech wireless keyboard. It works beautifully, once Ubuntu has started up. Grub doesn't recognize it, so I have to keep the old keyboard plugged in too for Grub's sake.
I plugged the transceiver into a USB port, booted up and everything, including it's special keys work. This thing was no doubt, designed for a Windows environment, yet when I press the email button, evolution is launched for me. If I press the home button, up comes Firefox!
Who told it what to do?
Presumably the keyboard driver gets told what combination of keys are being pressed and somewhere, a response for special keys must be stored. Does Ububntu recognize the keyboard plug and play style and then have a standard set of responses to key combinations?
Sorry if this sounds dumb, but "I cut my teeth on punched cards. Let me tell you about those days ...". I still think in terms of writing $20 to the interrupt processor chip to re-enable interrupts and things. I only have a very sketchy idea of how one talks to USB devices.

---

### Post by CatKiller on 2009-07-15
> **gwm said:**
>  Presumably the keyboard driver gets told what combination of keys are being pressed and somewhere, a response for special keys must be stored. Does Ububntu recognize the keyboard plug and play style and then have a standard set of responses to key combinations?

That's pretty much how I understand it. You can change settings with the System -> Preferences -> Keyboard Shortcuts tool. What actually get launched by a command like "launch media player" is set by your Preferred Applications preferences, and the channel that gets controlled with volume hotkeys is set by the sound configuration tool.

I believe that X needs to know some things about the keyboard you're using for it to happen automagically - knowing which signal should correspond to which special keypress, for a start - but I'd imagine that the weight of Microsoft has pressed keyboard manufacturers to some kind of consistency. Other signal interpretation methods probably get implemented as the devs get access to hardware information, so hotkeys might not work in one release but would work in a later release. And you can add your own shortcuts by pressing the appropriate button if it doesn't just work straight away.

Personally, I never use search, so using that button to show my Home folder instead is much more useful.

---

