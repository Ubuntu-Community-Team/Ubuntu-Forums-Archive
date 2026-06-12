---
title: "Karmic Freezes on boot up *DURING* Splash screen"
date: 2010-02-14
forum: General Help
---

### Post by tomcuk123 on 2010-02-14
Hi,
I am a comlete NOVICE at this!

I set up a dual boot on my laptop a few days ago, between Windows XP and Ubuntu 9.10 (installed from Live CD). All the hardware is working fine.

Anyway, SOMEtimes, during the splash screen , the screen turns off (physically turns off) and the hard disk seems to stop.
I cant do anything appart from force it to power down.

Yet sometimes, it boots up fine.

What could be the problem?
How could I fix it?

I want Ubuntu to work first time EVERY time.

Thanks in advance,
Tom

---

### Post by cariboo on 2010-02-14
Does your system actually freeze up, or is it that you just can't see the login screen?

---

### Post by mypalfootfoot on 2010-02-17
Have you found a fix for this? I am having the same trouble with my set-up, I can boot recovery mode and then startx and it works fine, it even runs fine from the livecd but for some reason it complete locks up at the gdm splash screen (not the usplash)... I can even alt+sysrq+r+s+e+i+u+b to reboot I have to hard reset. My system is a msi mainboard with dual amd athlon processors and an nvidia geforce fx5500, I suspected acpi might have been causing it but I am unsure.

Thanks

---

### Post by TabletUbuntu on 2010-03-01
I have had a similar problem.  My Toshiba Portege laptop will "randomly" (on average every third boot) freeze during boot.  CTRL-ALT_DEL will cause the system to restart.

 I disabled the splash screen on boot to see if I could identify the problem.  At first the last message before freeze had something to do about modem-manager plugins; uninstalling modem-manager got rid of these messages but not the problem.  Now, the last message that appears is something to the effect "nm-dispatcher.action: Script /etc/NetworkManager/dispatcher/01ifupdown exited error status 1.".  However, I'm not certain that this has anything to do with the actual problem.

I have done a lot of research on this problem and have turned up nothing.

---

