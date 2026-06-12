---
title: "Enable compiz on a Core i5 (Arrandale) based laptop"
date: 2010-12-02
forum: General Help
---

### Post by eshwar_andhavarapu on 2010-12-02
Hi,
I am trying to enable compiz desktop effects on my laptop but it keeps saying effects could not be enabled.  I am not sure what is the cause since other people on the forums have said effects work fine on the newer intel graphics chipsets. Is there an updated, method to enable them? Special xorg.conf, etc?

I am not sure what i need to attach so for now I am going to start with <code>lspci</code> and <code>/var/log/Xorg.0.log</code>

I am not sure if hybrid graphics causes this issue. Especially since in ubuntu only the intel graphics chip is active.

I have also asked on askubuntu.com. tried searching google, but no conclusive guide :(

[http://askubuntu.com/questions/15471/enable-compiz-on-intel-core-i5-nvidia-gt330m-based-laptop-on-lucid]("http://askubuntu.com/questions/15471/enable-compiz-on-intel-core-i5-nvidia-gt330m-based-laptop-on-lucid")

Please help me?

---

### Post by eshwar_andhavarapu on 2010-12-07
> **eshwar_andhavarapu said:**
> Hi,
I am trying to enable compiz desktop effects on my laptop but it keeps saying effects could not be enabled.  I am not sure what is the cause since other people on the forums have said effects work fine on the newer intel graphics chipsets. Is there an updated, method to enable them? Special xorg.conf, etc?

I am not sure what i need to attach so for now I am going to start with <code>lspci</code> and <code>/var/log/Xorg.0.log</code>

I am not sure if hybrid graphics causes this issue. Especially since in ubuntu only the intel graphics chip is active.

I have also asked on askubuntu.com. tried searching google, but no conclusive guide :(

[http://askubuntu.com/questions/15471/enable-compiz-on-intel-core-i5-nvidia-gt330m-based-laptop-on-lucid](http://askubuntu.com/questions/15471/enable-compiz-on-intel-core-i5-nvidia-gt330m-based-laptop-on-lucid)

Please help me?

        I  managed to get compiz to work. i uninstalled nvidia's proprietary driver  (nvidia-current). now with nouveau, glxinfo gives decent output and  says direct rendering is enabled (turns out its talking about the intel  chip). then i go to desktop effects, and when i select extra, it says  install nvidia proprietary drivers, i click cancel, the screen blinks  but compiz is now enabled.

Also updated the askubuntu.com question to reflect the answer

---

