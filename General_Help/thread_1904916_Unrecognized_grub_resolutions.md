---
title: "Unrecognized grub resolutions"
date: 2012-01-05
forum: General Help
---

### Post by Xgen on 2012-01-05
Any way to force grub (or burg) to recognize resolutions for my 16:9 laptop screen? Using a ATI Radeon card (6970) and the recognized ones (through hwinfo --framebuffer) are 4:3 and everthing but...

---

### Post by bluexrider on 2012-01-05
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer sudo apt-get update && sudo apt-get install grub-customizer
```

Try this customizer

---

### Post by Xgen on 2012-01-05
Busy site...threads disappear quite fast. Thanks for your answer, looks like a handy tool, but the Customizer only lists what is under the framebuffer query. My ATI card recognizes the 16:9 resolution in Catalyst and it is recognized in grub in other machine with an NVidia card. Eventually I will find a solution...:)

---

