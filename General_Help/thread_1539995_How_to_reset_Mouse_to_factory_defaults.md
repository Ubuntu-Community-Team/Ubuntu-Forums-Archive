---
title: "How to reset Mouse to factory defaults"
date: 2010-07-27
forum: General Help
---

### Post by HamletDRC on 2010-07-27
I am on 10.4 with a Dell Notebook (E6400). I use it mostly with a USB mouse. 

Everything worked fine for about 2 months. Then I shutdown, unplugged the mouse, restarted without the mouse, and my trackpad is broken. It works a little, but text fields and some apps capture the mouse events and won't let go. For instance, the cursor gets stuck in a text field and there is no way (keyboard or mouse) to get out. 

I've tried several times to fix this and I cannot. 

If I boot from a LiveCD then everything works fine. 

My theory is that the mouse configuration files somehow got corrupted in my plugging/unplugging of the external mouse. 

How can I reset the mouse to factory defaults? Are there a set of files I can copy over from the live CD?

UPDATE: I tried to delete and recreate my xorg.conf file and this did not work either.

---

### Post by dino99 on 2010-07-27
into synaptic: remove/purge "xserver-xorg-input-mouse" then reinstall it immediatly

---

### Post by HamletDRC on 2010-07-27
Here is what finally worked: 

Deleted /etc/X11/xorg.conf file
Reboot
run: sudo nvidia-xconfig
Reboot
Log Off
Log On

And then it works fine again... for now. I have _no_ idea why the log off then log on at the end was needed but it was. :(

---

