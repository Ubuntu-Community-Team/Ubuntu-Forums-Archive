---
title: "Error when I put in my graphics card"
date: 2006-05-09
forum: General Help
---

### Post by gRiMgRaVy014 on 2006-05-09
Well I think I have the Bus Id set to where my graphics card is located. I found it out by reading the error status when its set up wrong.Well anyway this is the error when I have the NV driver selected, and my nVidia Geforce 5500 card in:

**NV (0) Failed to open frame buffer device**
Kinda Confusung since I have no idea what the frame buffer device is :???:

---

### Post by johnc4510 on 2006-05-09
Not sure about frame buffer, but I have the same card and use the glx driver:
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
ctrl+alt+backspace to restart x
Mine works perfectly

---

### Post by gRiMgRaVy014 on 2006-05-11
*bump* please i really need to get this graphics card going, I might be going ot a counter striek LAN this weekend.

---

