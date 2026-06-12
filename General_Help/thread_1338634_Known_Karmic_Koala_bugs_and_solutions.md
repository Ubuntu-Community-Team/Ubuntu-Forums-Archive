---
title: "Known Karmic Koala bugs and solutions"
date: 2009-11-26
forum: General Help
---

### Post by elliotn on 2009-11-26
It would be nice if admin would make a post like this for 9.10 just like that one for 9.04 


Since I installed karmic I have never had sound, i have two sound cardsg lspci recognises them. Please help

---

### Post by 1Nadie on 2009-11-26
I don't know if Ur problem is similar to mine, but Kardom speakers did not work at the beginning of my instalation, so I went to sound and fix the out put to make the speakers work, now i got sound, btw, the speaker are plug into usb port..

---

### Post by elliotn on 2009-11-26
> **1Nadie said:**
> I don't know if Ur problem is similar to mine, but Kardom speakers did not work at the beginning of my instalation, so I went to sound and fix the out put to make the speakers work, now i got sound, btw, the speaker are plug into usb port..

i have reinstalled 3 times bt still nothing while all works with win xp or 9.04

---

### Post by elliotn on 2009-11-26
Now am wonderin should i b stuck wit 9.04

---

### Post by michaelzap on 2009-11-26
I posted my bugs and the solutions I was able to find [here]("http://ubuntuforums.org/showthread.php?p=8351419#post8351419").

I also had no sound when I installed Karmic. Disabling my proprietary modem driver got me stereo sound, and using the Lucid RC kernel and editing /etc/modprobe.d/alsa-base got me 5.1 sound. I still can't suspend or hibernate my laptop, however.

Given that Karmic was completely uselessly unstable when I started out and now I'm relatively happy with how it's running, those tips might help someone else.

---

