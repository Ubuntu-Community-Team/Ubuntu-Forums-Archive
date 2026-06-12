---
title: "Ubuntu 8.10 Graphics card doesn't work"
date: 2009-07-27
forum: General Help
---

### Post by eUsha on 2009-07-27
Hello,

I have been using Ubuntu with my ATI graphics card for sometime now. But I'm still not fluent with Linux. Recently I had to send back my motherboard for replacement of a better one. This one has an onboard graphics card.I was able to install drivers for windows xp but when I start Ubuntu, my monitor goes to sleep, meaning there is no input going to the monitor. All I get is a black screen. So If I can't even get ubuntu to start how can I install the drivers. 

Just in case it is important, when I start ubuntu I get the Kernel Alive message.

I would really appreciate if someone could help me.

Thanks

---

### Post by komputes on 2009-07-27
Are there any binary drivers available when you go to System > Administration > Hardware Drivers ?

If not, it would be helpful to know what card you have. Run the following command and copy-paste the output line relevant to your video card in you next comment.

```

$ lspci -nn
```

---

### Post by eUsha on 2009-07-27
Hi Komputes,

I can't get into Ubuntu. The screen is blank. The card is built into my motherboard. The motherboard is from Asus.

Thanks,

---

### Post by t4thfavor on 2009-07-27
What kind of card is listed on the box the mobo came in? It's either going to be Intel, ATI, or Nvidia.

Yo could try hitting escape when the grub menu appears, and then select recovery mode. From there you can do a dpkg-reconfigure xserver-xorg to reset the config for your card. Just be sure to backup the old one just in case you do more harm than good.

---

### Post by eUsha on 2009-07-27
Motherboard is a replacement so it did not come with normal packaging and CD's. Only the hardware was sent to me. But the chipset is Nvidia, So were the chipset drivers and so were the XP graphics drivers that I downloaded from Asus's website. So I believe the card on board is Nvidia. I'm using HDMI-to-DVI adapter to connect this card to my monitor. Since the monitor accepts DVI.

---

### Post by komputes on 2009-07-27
> **t4thfavor said:**
> select recovery mode. From there you can do a dpkg-reconfigure xserver-xorg to reset the config for your card.

That's been replaced with the xfix menu item. Are you able to get to the recovery menu? If yo you can drop to root shell and run the command given previously to find the make/model of the video card.

---

