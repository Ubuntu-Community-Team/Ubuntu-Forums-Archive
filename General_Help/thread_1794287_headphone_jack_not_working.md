---
title: "headphone jack not working"
date: 2011-06-30
forum: General Help
---

### Post by dtMeta on 2011-06-30
Hi, I have ubuntu 11.04 dual boot with vista in a gateway laptop.  The internal laptop speakers work fine, but anything I plug into the headphone jack does not work (I have headphones and speakers that I use through the headphone jack).

I've tried a ton of things like re-installing pulse, alsa mixer, making sure everything is turned up and NOT muted, and I can't get any sound.  please help!

EDIT: here is the alsa info script output...

[http://www.alsa-project.org/db/?f=a329789179bef8fc356021f70e2d6c591ad1d740](http://www.alsa-project.org/db/?f=a329789179bef8fc356021f70e2d6c591ad1d740)

**UPDATE-SOLVED**: Ok I finally found something that solved my issue. For any future gateway users that may read this -- try this fix here (I'm using an M model, the fix is for a T model, it worked anyway).

[http://ubuntuforums.org/showthread.php?t=1250802]("http://ubuntuforums.org/showthread.php?t=1250802")

which leads to:

[http://blog.wessendorf.org/2009/05/headphones-with-ubuntu-904-and-gateway-t-6345u/]("http://blog.wessendorf.org/2009/05/headphones-with-ubuntu-904-and-gateway-t-6345u/")

specifically to add this line to alsa.conf:

```
options snd-hda-intel model=eapd probe_mask=1 position_fix=1
```

you can open alsa.conf with this:

```
sudo nano /etc/modprobe.d/alsa-base.conf
```

---

### Post by Yellow Pasque on 2011-06-30
This might be relevant as it's a Gateway M-series with the same codec as yours: [http://www.linuxforums.org/forum/coffee-lounge/154383-take-sigmatel-stac9205.html](http://www.linuxforums.org/forum/coffee-lounge/154383-take-sigmatel-stac9205.html)

This is what I would try first:
```
echo "options snd-hda-intel model=eapd" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

---

### Post by dtMeta on 2011-06-30
Perfect timing.  That's exactly what worked!  Thanks you :)

---

### Post by Kakalle on 2011-07-12
...

---

