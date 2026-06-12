---
title: "Nvidia Graphics Card capable of using plymouth themes"
date: 2010-11-30
forum: General Help
---

### Post by 0N3 on 2010-11-30
Ive tried various different plymouth themes but cant see to use them. All i keep getting is an ugly Ubuntu 10.10 in text mode during boot up even i selected the plymouth theme.

Ive done 

sudo update-alternatives --config default.plymouth

Selected both 0 + 1 and it still doesnt change

  0            /lib/plymouth/themes/INT2MIL-Ubuntu-10.10-Eng/INT2MIL-Ubuntu-10.10-Eng.plymouth   100       auto mode
* 1            /lib/plymouth/themes/INT2MIL-Ubuntu-10.10-Eng/INT2MIL-Ubuntu-10.10-Eng.plymouth   100       manual mode

As you can see 1 is selected and it made no change to my PC i got no errors installing it all went smoothly. 

its a Geforce GT240M 1GB Graphics card surely its capable.
nVidia Corporation GT216 [GeForce GT 240M] (rev a2)

---

### Post by sikander3786 on 2010-11-30
There have been quite a few problems since Ubuntu adopted plymouth.

Rather than a fix, there is a workaround for 10.10.

[http://linuxhub.net/2010/09/fix-ugly-plymouth-screen-on-ubuntu-10-10-using-a-simple-script/](http://linuxhub.net/2010/09/fix-ugly-plymouth-screen-on-ubuntu-10-10-using-a-simple-script/)

---

### Post by 0N3 on 2010-11-30
That sorted it gonna try a few more different plymouth theme that wasn't as nice as i expected 

Thanks for the helped

---

### Post by Dans564 on 2010-11-30
I have tried every Plymouth fix/workaround on the web and although plymouth is displayed it is low resolution and doesn't fill my entire screen :/  I've learned to except it....

---

### Post by 0N3 on 2010-11-30
Use startup-manager to change the ressolution i did my resolution was terrible i tinkered with it and got it right.

---

### Post by Dans564 on 2010-11-30
yea I have tried that before.....  I think it just my computer cause even bios doesn't fill the screen.

---

### Post by 0N3 on 2010-11-30
[http://zorin-os.webs.com/splashscreenmanager.htm](http://zorin-os.webs.com/splashscreenmanager.htm) 

Just found that programme was so easy to switch themes installed mine perfectly jusy cop the folder with the plymouth theme in it to /lib/plymouth/theme/

Let the software do the rest was that easy got a gorgeous acer splashscreen installed now :)

---

