---
title: "ripping mp3 in k3b"
date: 2012-07-10
forum: General Help
---

### Post by Ben Aur on 2012-07-10
k3b in new Ubuntu installation offers only wav and ogg-vorbis as file types. How do I make it rip to mp3?

---

### Post by ron999 on 2012-07-10
> **Ben Aur said:**
> How do I make it rip to mp3?
Hi
Make sure K3b is installed properly with the correct codecs.
This command will do it:-
```
sudo apt-get update && sudo apt-get -y install flac k3b lame libk3b6-extracodecs
```
:cool:

---

