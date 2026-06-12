---
title: "how can i switch video cards?"
date: 2010-09-07
forum: General Help
---

### Post by ZeroSforza on 2010-09-07
i started to use ubuntu and i must say im impressed with it only one thing i want to know how to switch video cards because i have two video cards and the onboard one is to weak to manage ubuntu but the pci one is strong enough to support ubuntu i want to know how can i disable my onboard vid card and use my pci video card

---

### Post by wojox on 2010-09-07
Is there anywhere in BIOS to switch it?

---

### Post by utnubuuser on 2010-09-07
Yeah, sometimes you can select which is the primary video card in BIOS, (usually F2 at boot), and sometimes it's an automatic selection as soon as a card is inserted in the pci slot.

---

### Post by ZeroSforza on 2010-09-07
> **utnubuuser said:**
> Yeah, sometimes you can select which is the primary video card in BIOS, (usually F2 at boot), and sometimes it's an automatic selection as soon as a card is inserted in the pci slot.

i tried that and it goes to a black screen and this chain of errors show up and btw if you want to know what graphics card it is its a nvidea geforce 6200 (series 6)

---

### Post by wojox on 2010-09-07
Try reconfiguring xorg.conf

```
sudo nvidia-xconfig
```

```
gksudo nvidia-settings
```

---

### Post by cariboo on 2010-09-07
Xorg 1.9 supports video card switching, but it is only available for Maverick (10.10) unless you want to compile it your self. Maverick will be released on 10.10.10.

---

### Post by ZeroSforza on 2010-09-08
i actually got a picture of the error it gives me when i switch to my pci graphics card hope this helps

---

### Post by ZeroSforza on 2011-02-14
> **ZeroSforza said:**
> i actually got a picture of the error it gives me when i switch to my pci graphics card hope this helps

can anyone explain that one?

---

### Post by Yellow Pasque on 2011-02-14
kernel panic after switching to pci card? Are you sure the card is okay? Can you boot to a recovery console?

---

### Post by ZeroSforza on 2011-02-14
yea the cards ok and im not able to boot to a recovery console

---

### Post by ZeroSforza on 2011-02-14
im no expert on linux but could it be that ubuntu does not support the nvidea series 6 card (6200)?

---

