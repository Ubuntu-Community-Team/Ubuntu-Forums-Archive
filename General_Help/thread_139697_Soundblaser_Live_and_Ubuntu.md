---
title: "Soundblaser Live and Ubuntu"
date: 2006-03-04
forum: General Help
---

### Post by marlun on 2006-03-04
Hello!

I'm having problem with my sound on my Ubuntu computer. I've got a Soundblaster Live soundcard. I've got sound when playing music through XMMS. However I would prefer to use Rythmbox since it comes by default with Gnome. In Rythmbox I don't have any sound.

I got sound to work with XMMS by changing output plugin and then inside the output plugin options change to SBLivein the options that are there.

How can I change that for Rythmbox?

Another thing, I don't think the soundcard work in Ubuntu in general. Shouldn't there be a sound when I login for example? Theres no sound anyway right now, except for when I play radio in XMMS.

Thanks in advance for any answers!

-Martin Lundberg

---

### Post by steve.horsley on 2006-03-04
I had an SB Live card in my last PC. No probs with any Linux except that on first install, the default was often to use the onboard sound chio instead. Try System->preferences->sound and make sure that the default sound card is the SB Live.

---

### Post by marlun on 2006-03-05
Hello Steve!

You are right and so was my friend who helped me yeasterday. It was the OnBoard Audio Controller that was used by default. I went into BIOS and disabled it and now the sound works.

Thank you both! =)

---

