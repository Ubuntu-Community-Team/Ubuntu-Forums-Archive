---
title: "Change Volume Adjustment Channel"
date: 2010-10-06
forum: General Help
---

### Post by Skrying on 2010-10-06
Not sure that subject makes a ton of sense but here we go...

I've had an annoying problem with Ubuntu on my laptop for a bit. In Windows the volume for the speakers and the headphone jacks are controlled separately. This is wonderful because I can keep my speakers always muted and have my headphone channel set at the correct volume. Makes my life easier, I don't have to remember to mute my laptop all the time and worry about what noise could come out of it in public.

In Ubuntu the the volume adjustment slider always controls the "Master" channel. Which when I open up alsamixer in Terminal shows that this is controlling both the Master and Headphone channel. My laptop has two headphone out jacks, one which stays with the volume of the speakers and another that does not (shown as Headphone 1 in alsamixer). The one that does is the one being changed along with Master. So my goal here is to either have Ubuntu recognize when I plug in my headphones into the "unique" headphone channel to adjust only that channel and when I don't have headphones in that jack to adjust the other channel. If that doesn't work then I wouldn't be opposed against simply being able to permanently mute my speakers and just control the Headphone 1 channel volume.

If I adjust the channels in alsamixer I can actually accomplish my goal, but as soon as I change the slider in the indicator panel I'm back to the slider screwing everything up.

Laptop is a Dell XPS M1330 currently running 10.10 RC but this issue was also in 10.04. I'm posting in this forum because this issue seems entirely a software one, or rather a configuration problem that I'm not sure how to fix.

Any help or suggestions? Much thanks.

---

