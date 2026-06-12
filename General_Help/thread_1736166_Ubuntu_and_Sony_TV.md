---
title: "Ubuntu and Sony TV"
date: 2011-04-22
forum: General Help
---

### Post by barnesy on 2011-04-22
Hi Guys,
I just recently connected my Ubuntu computer to my Sony Bravia 46' television.  It works but I'm having a bit of an issue.  Ubuntu sees my tv as an 72' television and not a 46'.

Is there a way to change this somehow?

Thanks for the help!!

---

### Post by dino99 on 2011-04-22
which exact tv model ? wich graphic card ?

into a terminal:

sudo rm /etc/X11/xorg.conf
sudo update-pciids && sudo update-usbids
sudo dpkg --configure -a

---

### Post by barnesy on 2011-04-22
> **dino99 said:**
> which exact tv model ? wich graphic card ?

into a terminal:

sudo rm /etc/X11/xorg.conf
sudo update-pciids && sudo update-usbids
sudo dpkg --configure -a


Thanks for getting back!

My tv is a Sony KDL-46EX500
My graphic card is a Radeon HD 5550.

---

### Post by dino99 on 2011-04-22
how are settings into the menu: system prefs screen ?

---

### Post by Claus7 on 2011-04-22
Hello,

> **dino99 said:**
> which exact tv model ? wich graphic card ?

into a terminal:

sudo rm /etc/X11/xorg.conf
sudo update-pciids && sudo update-usbids
sudo dpkg --configure -a

just to point out that instead of removing the xorg.conf file a better idea would be to do:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Regards!

---

### Post by CoolJohnB on 2011-04-22
I have a similar problem with my 39" LG TV, it is seen as a 52" screen, but having said that it doesn't seem to effect anything!  So I just ignore it.

---

### Post by barnesy on 2011-04-23
I tried both suggestions and I get "no such file".

Am I doing something wrong?

Thanks for the help!!

---

### Post by Claus7 on 2011-04-23
Hello,

> **barnesy said:**
> I tried both suggestions and I get "no such file".

Am I doing something wrong?

Thanks for the help!!

it seems that your installation of ubuntu does not require any xorg.conf file so as to work ok. 

Which does not mean that your tv screen is recognised with the resolution it should. I have not any experience on that, so aside from bumping your thread that way, I would ask:

where is it supposed to be recognised your tv with '??' resolution from ubuntu. That way, by giving this info, I might be able to give some help.

...Also, while having connected your tv, if you type:
```
sudo aticonfig --initial -f
```

does this (after rebooting ubuntu) solve your issue?

Regards!

---

### Post by barnesy on 2011-04-26
> **Claus7 said:**
> Hello,



it seems that your installation of ubuntu does not require any xorg.conf file so as to work ok. 

Which does not mean that your tv screen is recognised with the resolution it should. I have not any experience on that, so aside from bumping your thread that way, I would ask:

where is it supposed to be recognised your tv with '??' resolution from ubuntu. That way, by giving this info, I might be able to give some help.

...Also, while having connected your tv, if you type:
```
sudo aticonfig --initial -f
```does this (after rebooting ubuntu) solve your issue?

Regards!


Thanks for the help.  I tried this but it aticonfig unknown command.

I ended up going into the additional drivers and it wanted to run an update on my ATI card.  I did the update, rebooted and it works now.  It sees the TV as an "Unknown" but at least it fully fits the screen and everything seems to be working fine.

Thanks again for all the help!

---

