---
title: "Cant get mic to work"
date: 2009-06-27
forum: General Help
---

### Post by RedSingularity on 2009-06-27
For some reason i cannot get the mic to work.  The sound in the headset works fine.  (Its an analog headset with the separate mic and earphone plug.)  I have not a clue whats going on.  Any input would be helpful.  Thanks.

---

### Post by RedSingularity on 2009-06-29
I say BUMP!!!!!

---

### Post by t4thfavor on 2009-06-29
One woud hope that someone with 1000 some posts would know we need more info about your setup. Its pretty easy to get a mic working especialy on older hardware, while  its also pretty easy to render your sound broken if you do something wrong.

I always try another port, or if your using the headphone port, make sure the headphone heck mark is on, and that you are using front mic for your source. Also chek alsamixer and make sure its not muted still.

Hope this helps.

---

### Post by RedSingularity on 2009-06-29
Ahh it was an ignorant mistake on my part as usual.  I had the mic on mute in the config settings.  Thanks though.

---

### Post by t4thfavor on 2009-06-29
See I helped, even though it was a small mistake I still feel better about it.

---

### Post by viljun on 2009-06-29
Bump.

I'm not maybe the best to help but you might try these ...

Check if the mic works with other machine, Windows or with stereos or PA if possible - some mics are easy to break. Also check it's on the right port in your audio card - try all ports if not sure. Don't forget put your mic on if it has a button. Also check the plug is connected properly.

Install for example audacity (apt-get install audacity) and click the arrow besides the mic icon, monitor the input and yell hard: "my neighbors are idiots". Check if the meter moves. Also click record button and then listen carefully if you get something or not.

Check your mic level is up: right click speaker icon on your desktop bar and select open volume control. Also check the mic is not muted.

You may also want to play with /dev/dsp. Something like this may work:
cat /dev/dsp > sound.raw (talk to mic and the press ctrl-c when done)
cat sound.raw > /dev/dsp (should play it back)

---

