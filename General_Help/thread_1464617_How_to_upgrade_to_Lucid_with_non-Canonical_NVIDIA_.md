---
title: "How to upgrade to Lucid with non-Canonical NVIDIA driver?"
date: 2010-04-28
forum: General Help
---

### Post by martini1179 on 2010-04-28
I've been using an NVIDIA driver from NVIDIA's site (190.53) for a while. Now I want to upgrade to Lucid. 

1) Is it recommended to uninstall this driver prior to upgrading to Lucid? 

2) If yes, how do I go about this? Please be specific, since I don't want to presume anything and make a mistake.

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
Yes... uninstall. You can just run the nvidia-blah-blah-195.8.3.sh file again to do it.

---

### Post by klemes on 2010-04-28
Simply in the section Driver in your xorg.conf substitute "nvidia" with "nv"
so as to use the open source driver from the official repos.
There is an --uninstall switch in the package that you downloaded from nvidia web site but you don't neeed to go go through this procedure.After the upgrade if you still want to use the proprietary driver you will have to run that package again and reinstall the driver and also manually edit your xorg.conf once again so as to use the "nvidia" driver"
or let sudo nvidia-xconfig do it for you.:guitar:

---

### Post by dino99 on 2010-04-28
> **martini1179 said:**
> I've been using an NVIDIA driver from NVIDIA's site (190.53) for a while. Now I want to upgrade to Lucid. 

1) Is it recommended to uninstall this driver prior to upgrading to Lucid? 
[COLOR="Blue"]users often update over the previous release without trouble, but might uninstall first with synaptic (purging) and change "nvidia" to "nv" or "vesa" into /etc/X11/xorg.conf, then reboot[/COLOR]


2) If yes, how do I go about this? Please be specific, since I don't want to presume anything and make a mistake.

[COLOR="Blue"]the next step is to clean your system before a dist-upgrade:
- into synaptic -> repo: uncheck all third party and ppa if you have, and change "karmic" to "lucid" on every official ubuntu repo.
- install and run gconf-cleaner
- then sudo apt-get clean && sudo apt-get autoclean && sudo apt-get autoremove && sudo apt-get install -f

- now you can update: sudo apt-get dist-upgrade  and reboot

booting with lucid, check that nvidia-current is activated ( system - admin - hardware driver), if not : delete xorg.conf as lucid dont need it by default and into synaptic you might have: nvidia-current and nvidia-current-modaliases installed with 195.36.15 driver, you can add nvidia-settings if you want.[/COLOR]

---

### Post by martini1179 on 2010-04-28
Thanks for the advice, guys. 

I decided to uninstall the driver using the --uninstall switch, then upgrade to Lucid. 

But now I'm in "low graphics mode".  Normally I'd just reinstall the non-canonical nvidia driver to fix this, but I want to upgrade to lucid first (to avoid any potential problems).  

How do I go back to the nv driver now? Is it still just a matter of editing xorg.conf and replacing "nvidia" with "nv" under "Section Device"? 

If so, what, if anything, do I put for "VendorName"?

---

### Post by dannyboy79 on 2010-04-28
resolve what? what does it matter that you're in low graphics mode prior to the install? i would say you should go ahead with the upgrade, then after fully upgraded. you can then install nvidia-current as stated above. good luck

---

### Post by philinux on 2010-04-28
> **martini1179 said:**
> I've been using an NVIDIA driver from NVIDIA's site (190.53) for a while. Now I want to upgrade to Lucid. 

1) Is it recommended to uninstall this driver prior to upgrading to Lucid? 

2) If yes, how do I go about this? Please be specific, since I don't want to presume anything and make a mistake.

I've just done a clean install of the daily build. 

Hardware drivers has installed this version. nvidia-current 195.36.15 ;).

Looks up to date enough to me and painless install.

---

### Post by martini1179 on 2010-04-28
> **philinux said:**
> I've just done a clean install of the daily build. 

Hardware drivers has installed this version. nvidia-current 195.36.15 ;).

Looks up to date enough to me and painless install.

  That's great, but I don't see how that answers any of my questions or helps me.

---

### Post by philinux on 2010-04-28
> **martini1179 said:**
> That's great, but I don't see how that answers any of my questions or helps me.

Ah ok. I never upgrade as I've always had problems. If you upgrade you get a new kernel. That will uninstall the nvidia driver anyway as that always happens when there is a new kernel unless one installed the repo version. You may have noticed such.

---

### Post by dannyboy79 on 2010-04-28
> **martini1179 said:**
> That's great, but I don't see how that answers any of my questions or helps me.

please see post #6 for an answer. maybe it's not the answer you want but it's AN answer.

---

