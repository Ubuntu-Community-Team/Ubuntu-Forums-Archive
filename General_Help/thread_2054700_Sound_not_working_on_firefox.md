---
title: "Sound not working on firefox?"
date: 2012-09-07
forum: General Help
---

### Post by MoarAwesomer on 2012-09-07
my sound works on everything else i've used but for some reason, firefox won't play sound from any source.
no speakers + no headphones, (please help)

---

### Post by Epodx64 on 2012-09-08
Try loading the PulseAudio mixer (I can't remember what it's called anymore I've been using Kubuntu for years GnomeMixer or something? ) and see if theres an option muted or turned down.

---

### Post by greatsirkain on 2012-09-08
alsamixer to make sure everything's turned up

Edit:
Make sure your flash is up to date too, a reinstall of flash might help if something is actually broken but first check that you have javascript enabled and hardware acceleration disabled from the firefox preferences, could also clear the firefox cache while you're there

---

### Post by MoarAwesomer on 2012-09-08
how to check javascript?

---

### Post by pqwoerituytrueiwoq on 2012-09-08
```
sudo su;echo -e 'pcm.pulse {\ntype pulse\n}\nctl.pulse {\ntype pulse\n}\npcm.!default {\ntype pulse\n}\nctl.!default {\ntype pulse\n}' >> /etc/asound.conf;exit
```
logout and login

---

### Post by MoarAwesomer on 2012-09-08
rebooted flash player was the problem, thanks guys!

---

