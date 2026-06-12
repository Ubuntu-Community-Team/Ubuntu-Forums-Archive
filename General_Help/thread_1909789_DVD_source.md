---
title: "DVD source"
date: 2012-01-15
forum: General Help
---

### Post by Airycat on 2012-01-15
When I put a DVD into my mom's computer it wont play. It looks for necessary plugin and says is can't find it. What it's looking for is "DVD Source." I've tried it in several players. None works. No DVD plays in the computer although they did before Ubuntu, to the best of my knowledge.

I have the codecs, as far as I can tell. 

It sounds to me like it isn't reading the DVD player (hardware) even though it shows the disk in the home files, but I don't know. I have no problem with this in my computer.

---

### Post by wildmanne39 on 2012-01-15
Hi, welcome to the forum! Have you installed the restricted drivers?

If not copy and paste this into a terminal ctrl+alt+t and enter your password.
```
sudo apt-get install ubuntu-restricted-extras
```
What application is trying to play the DVD?
Thanks

---

### Post by oldos2er on 2012-01-16
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Airycat on 2012-01-16
Thank you both! I got the DVD to be recognized and switched players* so that it doesn't play the intro over and over without continuing, but still no sound. The article referred to says 
> No Sound
If you don't hear any sound, click System -> Preferences -> Sounds. but where do I find that to click on it? I saw several files, starting with "File System," but none of them follow that line.

* Opened it in the VLC player, but it still automatically goes to the Movie Player when I load it. How do I correct that?

Sorry to be such a noob, but I gotta start somewhere. Is there an *Ubuntu for Dummies *available?

---

### Post by wildmanne39 on 2012-01-16
Hi, if you are using 11.04 or 11.10 ubuntu with unity click on the speaker in the top right corner of the screen>sound settings.

If that does not help here is a link to a sound guide.
[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit)

---

