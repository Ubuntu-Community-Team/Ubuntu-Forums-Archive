---
title: "No sound from right speaker"
date: 2011-02-11
forum: General Help
---

### Post by humturtle39 on 2011-02-11
Acer 5742 running Ubuntu 10.10. As far as I know I've not changed any of the sound defaults. I checked the output balance in the sound settings menu and that's not the problem. The right channel works fine with external speakers plugged in. The same speakers work fine in my Windows 7 partition so they're not broken.

Does anyone have any ideas what's wrong?

---

### Post by humturtle39 on 2011-02-11
Okay after a bit of googling I discovered the Acer 5742 has a mono speaker. I'm guessing this is the root of the problem but I'm not sure where to go from here.

In the sound settings menu, if I set the output balance to the right, I get no sound, and if I set it to the centre or left, I get sound but stereo sound is still missing the right channel.

---

### Post by atapia984 on 2011-02-12
I am experiencing the exact same issue. I have tried just about everything I could find googling around to fix it. The thing is that while on external (Altec Lansing) speakers, all sounds great. It could just be a hardware issue.

---

### Post by nslegacy163 on 2011-04-26
Same problem (Altec Lansing) 3.1...hilariously, I had sound in the right and little/none in the left and now it's switched. ](*,)

 Sorry this isn't a solution...just a bump.

---

### Post by zool--- on 2011-05-23
bump

same problem on a Dell's Inspiron m301z. The card is an HDA ATI SB.

C'mon guys, it's 2011, and Linux users _still_ have audio issues?

---

### Post by nslegacy163 on 2011-05-23
As far as altec lansing 2.1 sound goes, I fixed mine by swapping out the audio cable (green tipped little guy) and everything works fine for me.

---

### Post by rha1063 on 2011-09-05
Ditto, right channel missing. Works on external speakers. Works with Windows7. Broken in Ubuntu 11.04, Dell Vostro V13.


```
$ lspci | egrep -i aud
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```

Also, alsa-info.sh output [here]("http://www.alsa-project.org/db/?f=2d8ed2b32f3ecb0abbc0b991ceb1f58438dab644").

---

