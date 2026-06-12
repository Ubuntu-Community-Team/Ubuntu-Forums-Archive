---
title: "Screen blanks before log-in screen"
date: 2011-01-26
forum: General Help
---

### Post by Jopiexjoker on 2011-01-26
Last week, after installing the regular ubuntu updates, i had a problem. My screen blanked at start up just before the log-in screen should apear. The system is also completely stuck. CTRL-ALT-F* or CTRL-ALT-DEL both do not work.

The xorg.3.log had the following error:

xf860OpenConsole:
VT_WAITACTIVE failed: interrupted system call  

After the trouble this gave I've reinstalled ubuntu (keeping /home).

The first regular updates after reinstallation contained:
xserver-xorg-core:i386(1.9.0-0ubuntu7 1.9.0-0ubuntu7.3) 
xserver-common:i386(1.9.0-0ubuntu7 1.9.0-0ubuntu7.3)
xserver-xorg-input-evdev:i386 (2.3.2-6ubuntu3, 2.3.2-6ubuntu3.1)

And guess what. The same happened again after updating.

Starting in repair-mode and manually starting GDM also blanks the screen in the same way.

I'm running Ubuntu 10.10 maverick with ati radeon hd4650.

The following bugreport mentions the same issue, but doesn't give a satisfying answer.
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/441653](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/441653)

Can anybody help me out with this?

---

### Post by Krytarik on 2011-01-26
What video driver are you running? How did you install it?

Guide: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

Try re-installing the driver, boot into recovery mode -> root console before
- if installed as package (sudo isn't necessary here, since you are root):
```
apt-get install --reinstall fglrx
```- if installed manually, run the installer script

---

### Post by Jopiexjoker on 2011-01-26
> **Krytarik said:**
> What video driver are you running? How did you install it?

Guide: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

Try re-installing the driver, boot into recovery mode -> root console before
- if installed as package (sudo isn't necessary here, since you are root):
```
apt-get install --reinstall fglrx
```- if installed manually, run the installer script

I've installed the proprietary ati driver, downloaded from their website. (with the catalyst control centre)

It has a gui installer. I could reinstall from the low graphics mode (the option in the recovery mode menu).

I have read though that the mentioned error also occurs with intel and nvidia graphic-cards...

---

### Post by Jopiexjoker on 2011-01-26
I gave it a shot, and it worked! \\:D/

so it was really that simple?? :oops:

thanks for your help!

---

### Post by Krytarik on 2011-01-26
> **Jopiexjoker said:**
> I gave it a shot, and it worked! \\:D/

so it was really that simple?? :oops:

thanks for your help!
Eh, what have you done now? Installed "fglrx" instead?

---

### Post by Jopiexjoker on 2011-01-26
> **Krytarik said:**
> Eh, what have you done now? Installed "fglrx" instead?

No, i reran the ati installer in low graphic mode.

---

### Post by Krytarik on 2011-01-26
> **Jopiexjoker said:**
> No, i reran the ati installer in low graphic mode.
Ok, I thought that hasn't worked, following post #3.

EDIT: One advice: If you don't want to re-run the installer everytime the kernel gets updated, you may install the driver as package, remove the manually installed one before, following the install instructions.

---

### Post by Jopiexjoker on 2011-01-27
> **Krytarik said:**
> Ok, I thought that hasn't worked, following post #3.

EDIT: One advice: If you don't want to re-run the installer everytime the kernel gets updated, you may install the driver as package, remove the manually installed one before, following the install instructions.

Post #3 were my concerns before re-running :P

Fortunately it worked though.

But can I find the same proprietary ati packages (including CCC) in Synaptic ?

---

### Post by Krytarik on 2011-01-27
> **Jopiexjoker said:**
> 
But can I find the same proprietary ati packages (including CCC) in Synaptic ?
Yeah, it's called "fglrx", it's only one package, and it also includes ATI/AMD Control Center. But, like I said, try to remove the other one before, may not be really possible.

---

### Post by Jopiexjoker on 2011-01-27
Cool... I uninstalled the ati driver (following instructions) and now everything just works fine.. even with 3d effects.

No need to install fgrlx.. (?)

---

### Post by Krytarik on 2011-01-27
I really wonder how that is possible. Did you restart/relogin after removing the driver?
Check in "/var/log/Xorg.0.log" what driver gets actually loaded.

And yes, I see the need to install "fglrx", in either case.

---

