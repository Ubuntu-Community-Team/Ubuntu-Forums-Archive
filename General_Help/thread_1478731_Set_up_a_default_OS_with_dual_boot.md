---
title: "Set up a default OS with dual boot?"
date: 2010-05-10
forum: General Help
---

### Post by chaospoodle on 2010-05-10
I recently installed Ubuntu and I am dual booting it with Windows 7. I showed it to my friend and he likes it. He wants me to dual boot his computer with Ubuntu, also.

We were wondering if there was a way to configure GRUB and that stuff so that it doesn't go to the GRUB boot screen when you start your computer where you pick an OS. We were wondering if you could set a default OS that the computer automatically booted to, unless you press a button at startup, and then you could get to GRUB to pick a different OS.

The reason being is because his whole family uses the computer, and we don't want to confuse them with GRUB every time they start up the computer. We just want the computer to boot to Win7 by default, but being able to boot into Ubuntu if you press a button to get to GRUB when booting.

---

### Post by dino99 on 2010-05-10
look at grub 2 guide below

---

### Post by chaospoodle on 2010-05-10
I'm new to Ubuntu, just installed myself 2 days ago. I get confused at this part:
> [COLOR=DarkRed]Caution:[/COLOR] Holding down the "SHIFT" key will  not display the menu if "GRUB_TIMEOUT=" is set to "**0**" . To always  have this interrupt capability, the *keystatus* check in */etc/grub.d/30_os-prober*  can be copied to */etc/grub.d/40_custom* or to another script in  the same folder. The *keystatus* check introduces a short timeout  interruptible by the ESC key if the key status cannot be determined.

I'd like to have the timeout at 0 so you don't see GRUB by default, but the part about adding the keystatus to allow interrupting so you can boot into something else if needed.

Is what I linked even relevant to my goal?

Trying to get it to boot by default into Windows without GRUB showing, but having the option to hit something during boot to bring up GRUB when needed.

---

### Post by hariks0 on 2010-05-10
Try installing Startup Manager from Synaptic. The Grub will eventually show up though.

---

