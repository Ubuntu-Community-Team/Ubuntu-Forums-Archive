---
title: "Ubuntu Karmic 9.10 sound clicks"
date: 2009-12-13
forum: General Help
---

### Post by pmalvr on 2009-12-13
Hi,

I have a clean install of Ubuntu Karmic 9.10 and the sound makes constant and annoying clicks, especially with my headphones plugged in. Is this happening with someone else? There is any fix for this?

Thanks in advance.

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
Do you mean a pop when you fist start audio or constant clicking throughout? If it's the latter then it's more than likely a problem with your audio drivers or audio card so you should try to reinstall the drivers. If the former then comment out the last line of /etc/modprobe.d/alsa-base.conf and it will go away but your sound card will constantly be powered on.

---

### Post by pmalvr on 2009-12-13
Its a pop when I start the audio and also a constant pop when a have headphones plugged in the pc. And no, this is not a problem with my audio drivers or audio card, because my cousin, witch also have ubuntu 9.10 in a pc of a different brand, has the same issue.

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
See the alsa.conf fix in my previous post and mark as solved if it works. It should work. I just deal with the pop because without sleep mode available I need to save power where I can. Hope this helps.

---

### Post by GregBrannon on 2009-12-13
Sin@Sin may have nailed it, but check here for a more thorough discussion:

[http://ubuntuforums.org/showthread.php?t=1312690]("http://ubuntuforums.org/showthread.php?t=1312690")

Good luck!

---

