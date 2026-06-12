---
title: "Compiz Ubuntu Nvidia"
date: 2009-07-30
forum: General Help
---

### Post by MrCapuchino on 2009-07-30
Hello
I just installed Nvidia driver version version 180, it shows in hardware drivers and its working. I downloaded simple-ccsm, compiz fusion settings manager w/emerald, fusion-icon and still when I try to apply the desktop effects it shows me:

Desktop Effects Could Not Be Enable

I have used Compiz in OpenSuse and worked fine, still had problems installing it but at the end it worked, so what am I doing wrong, or what should I do to enable the compiz effects?

Thanks in advance, I'm using a dual booted vista ubuntu laptop with 2gb ram and a Nvidia 7000m videocard with a amd turion 64x2 proccessor, still Im using a 32 bit ubuntu 9.04 version

---

### Post by josephe on 2009-07-30
Hi 
I have a similar problem, loaded Ubuntu 9 and Compiz, everything seemed fine. Except when I shut down the machine the screen filled with thin horizontal lines. When I loaded a more recent driver for my Nvidia card and tried running AWE (Mac like object docker) I get " Screen not composited. Run Compis (-fusion) or similar compositing tool" .
 
When I try uninstall and reinstall Compiz and change a setting then AWE seems to work, but then I reboot and it's gone again!
 
Anyone have any ideas?
 
Thanks
My pc is  DEll Inspiron 1520 by the way

---

### Post by overdrank on 2009-07-30
> **MrCapuchino said:**
> Hello
I just installed Nvidia driver version version 180, it shows in hardware drivers and its working. I downloaded simple-ccsm, compiz fusion settings manager w/emerald, fusion-icon and still when I try to apply the desktop effects it shows me:

Desktop Effects Could Not Be Enable

I have used Compiz in OpenSuse and worked fine, still had problems installing it but at the end it worked, so what am I doing wrong, or what should I do to enable the compiz effects?

Thanks in advance, I'm using a dual booted vista ubuntu laptop with 2gb ram and a Nvidia 7000m videocard with a amd turion 64x2 proccessor, still Im using a 32 bit ubuntu 9.04 version
Hi and welcome, You may look at the FAQ's link in my signature and try compiz-check to help. Also you may try and disable and then install the nvidia driver again.
> **josephe said:**
> Hi 
I have a similar problem, loaded Ubuntu 9 and Compiz, everything seemed fine. Except when I shut down the machine the screen filled with thin horizontal lines. When I loaded a more recent driver for my Nvidia card and tried running AWE (Mac like object docker) I get " Screen not composited. Run Compis (-fusion) or similar compositing tool" .
 
When I try uninstall and reinstall Compiz and change a setting then AWE seems to work, but then I reboot and it's gone again!
 
Anyone have any ideas?
 
Thanks
My pc is  DEll Inspiron 1520 by the way
josephe Please do not hijack the thread with your issue. It sounds as your settings are not being saved. If you use the nvidia settings ```
gksu nvidia-settings
``` and save the settings hopefully this will correct your issue.

---

### Post by stlsaint on 2009-07-30
ensure that you are using the latest nvidia drivers and try updating compiz thru ultamix!

---

### Post by josephe on 2009-07-30
Hi guys
 
Thanks for the help and apologies if I hijacked the thread, I'm pretty new to this and honestly thought they might be related.

---

### Post by overdrank on 2009-07-30
> **stlsaint said:**
> ensure that you are using the latest nvidia drivers and try updating compiz thru ultamix!

Ultamatix :-#[-X

---

### Post by MrCapuchino on 2009-07-30
Thank you all for your help.

The problem was that I installed the driver first manually, then I installed a better driver using envyng without uninstalling the previous one, that caused conflicts, uninstalled all nvidia drivers then installed the one using envyng, everything works now.

Thank You for your Help.

---

