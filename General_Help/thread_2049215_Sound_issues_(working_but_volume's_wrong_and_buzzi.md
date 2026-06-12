---
title: "Sound issues (working but volume's wrong and buzzing)"
date: 2012-08-28
forum: General Help
---

### Post by Xenoty on 2012-08-28
Hello everyone :)

I have sound issues with my hp dv6 Ubuntu12.04 laptop.
I tested it with : Speakers, bose oe2 headphone, apple headphone, cheap headphone from airlines company.


The first issue is that when i play a song on speaker (beats audio) the volume is really much lower than on windows. It's not really a problem but it's strange.


The second issue is :
[IMG]http://s17.postimage.org/carmrugkv/Screenshot_from_2012_08_28_11_49_52.png[/IMG]
When i play a song and the volume is in the red zone i don't hear any song on speaker or any headphone but after the red zone, in the green one the sound is directly quite loud.


And the third issue, the really annoying one, is :

The song on headphone is buzzing on the background even if nothing is played. I would describe it as the noise of a bee plus the sound of sparkles from time to time. The strang.e thing is that it only happen with pricey headphone (bose or apple) not with cheap one.


Thank you in advance if you read everything i wrote and for any help :)
 I also would like to apologize for my english, i'm not native.

Xenoty

---

### Post by Mark_in_Hollywood on 2012-08-28
Xenoty:

Your English seems workable. No Worries!

If you can open a terminal and type:

alsamixer

expand that window so you can see all the configurable items and play with some and see if that resolves your problem, Great. If not, let us know.

---

### Post by Xenoty on 2012-09-01
Thanks for your help :) I tried your solution for a few days.

The first issue is resolved.

The second, i now understand what happen. For the red volume zone the computer change in alsamixer the PCM and Speaker volume . And i don't know why but if master=16 and speaker<90 i can't hear any song.


And for the third one, the buzzing, if i put all parameters to 0, i still hear it. BUt if I unplug the power cable it's stop :o . It's of course not a durable solution ..

Thanks again for your help :)

---

