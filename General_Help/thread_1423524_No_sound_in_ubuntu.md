---
title: "No sound in ubuntu?"
date: 2010-03-06
forum: General Help
---

### Post by kamilii on 2010-03-06
This is my first time running ubuntu and I really like it but when I went on youtube I noticed there was no sound?How can I get sound to work on ubuntu please help.I am running the newest version

---

### Post by kamilii on 2010-03-06
I just installed ubuntu for the first time and i noticed I had no sound,anyone know what the problem is?I'm running the newest version

---

### Post by mickey57 on 2010-03-06
sudo apt-get remove pulseaudio

sudo apt-get install esound

exit

---

### Post by Enigmapond on 2010-03-06
> **mickey57 said:**
> sudo apt-get remove pulseaudio

sudo apt-get install esound

exit

That's a bit rash for a new install. I would check all the sound devices rather than doing this. This is only for drastic cases. Open the alsa mixer and make sure all volumes are up...there are threads here to trouble shoot if you search. Don't uninstall pulseaudio unless it's absolutely the last thing....

---

