---
title: "Audacity - libmp3lame.so needed."
date: 2006-04-03
forum: General Help
---

### Post by wizzkid on 2006-04-03
Hi! I installed audacity for mp3 editor. after I cut mp3, and save it as mp3, it pormpt me that it couldnt find the libmp3lame.so.. i tried o find it but i cant... so can somebody help me? :) anybody encounter and solved this? :)

Thanks

---

### Post by Al3xanR0 on 2006-04-03
[QUOTE=wizzkid]Hi! I installed audacity for mp3 editor. after I cut mp3, and save it as mp3, it pormpt me that it couldnt find the libmp3lame.so.. i tried o find it but i cant... so can somebody help me? :) anybody encounter and solved this? :)

Thanks[/QUOTE]

apt-get install lame

---

### Post by localzuk on 2006-04-04
Also, you may need to ```
sudo apt-get install liblame0
```

---

### Post by chiefofthejojos on 2006-04-05
after you install install lame you will need to create a symbolic link like so:
sudo ln -s /usr/lib/libmp3lame.so.0 /usr/lib/libmp3lame.so

Then you can try the operation in audacity again, and browse to the /usr/lib/libmp3lame.so file.

---

### Post by ruffneck on 2006-04-12
awesome thanks!

---

