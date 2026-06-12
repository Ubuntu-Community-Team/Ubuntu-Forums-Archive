---
title: "What does a single &quot;X&quot; on screen means?"
date: 2010-05-01
forum: General Help
---

### Post by perstromgren on 2010-05-01
In order to fit an upgrade of 10.04 on my system (EEE 901) I moved some stuff from the root volume to a second volume. A bit too much, perhaps... I think I have moved it back, but my system does not boot (or log in) correctly. The last move was to symlink /var/cache/apt which seemed pretty safe. 

I only get a single X windows marker on the screen, and no reaction to the keyboard, what so ever.

Three questions

1. What could generate this problem, i.e. what program(s) is missing or not running?
2. How do I do fail safe boot?
3. Is there a "repair installation" tool somewhere to get my system back to some sane state?

I can boot from a USB stick and mount the failing system just fine. A fsck of the "bad" root file system shows no errors. I "think" I have everything back where it belongs, but I did remove some stuff with the synaptic tool, but only with "open office" in its name.

Sorry for being so vague, but it seems I am very near a correct boot, and I would rather not do a clean install, if I can avoid that.

Per.

---

### Post by tgalati4 on 2010-05-01
Is it the stylized X-Windows logo?

If so, then try to reset your X-windows environment.

Reboot into rescue (root console) mode, then type:

dpkg-reconfigure -phigh xserver-xorg

---

### Post by perstromgren on 2010-05-02
No, I was not very clear. It is the standard X windows cursor (I think, I haven't seen it a while). And it moves with my mouse, but that is the only response I can get. No clicking or any keys will make it react.

How do I reboot into rescue mode? When I hit ESC I only get a choice between to boot from the two disc partiions, nothing about any choice of kernel variants or any such. *EDIT: Spoke too fast. SHIFT is what I should have used. And it takes me into the GRUB menu OK. I make some more resaerch and come back.*

Perhaps GRUB is broken? Can I repair anything by booting from another media (USB works fine) and mount the broken disk?

Per.

---

### Post by perstromgren on 2010-05-02
More information.

First: CTRL+ALT+F1 switches from en empty screen with th "X" cursor to terminal, where I can log-in and everything works. 

I tried "startx", but the system tesll me that an X server is already running. What I still don't understand is why X does not continue and start the window environment.

To be continued...

Per.

---

### Post by tgalati4 on 2010-05-02
Well, you obviously moved some system files from their proper place (the root partition) to somewhere else.  Then you moved them back--but perhaps not all of them or not in the correct place.

When you break linux, you get to keep both pieces.

Back up your critical data, using the command line or using a Live CD.

Without knowing exactly what you moved, your only recourse is to reinstall.

Make sure you have enough space to install and grow your installation.  You need at least 10 GB for a minimal install and really 40 GB if you want room to add applications that eat up space like googleearth or games.

---

