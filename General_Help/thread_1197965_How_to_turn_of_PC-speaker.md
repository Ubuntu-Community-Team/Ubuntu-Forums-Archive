---
title: "How to turn of PC-speaker?"
date: 2009-06-26
forum: General Help
---

### Post by Nyhus on 2009-06-26
I've got a clean install of xubuntu on my new laptop, but cant seem to turn the pcspeaker of?

First i tryed this:
> WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
eivind@eivind-laptop:~$ cat <<END >>/etc/modprobe.d/blacklist> blacklist pcspkr
> blacklist snd_pcsp
> END
bash: /etc/modprobe.d/blacklist: Permission denied

When i didnt get access i tryed with "gksu thunar" and adding blacklist "pcspkr" and blacklist  "snd_pcsp" to blacklist.conf . This didnt work either. 

Suggestions?

---

### Post by philcamlin on 2009-06-26
do you mean the beep?

rmmod pcspkr

thats what you want

---

### Post by Ayuthia on 2009-06-26
Does:
```
sudo modprobe -r pcspkr
```
Stop it?  If it does, then we can double-check your blacklist.conf file.  It might just be a matter of updating your initramfs (sudo update-initramfs -u).

---

### Post by Nyhus on 2009-06-26
> **philcamlin said:**
> do you mean the beep?

rmmod pcspkr

thats what you want

I've tryed this, works till i restart, then same problem. And yes, i guess its the beep i think.

> Does:
 	Code:
 	sudo modprobe -r pcspkr 
Stop it?
Will try this and get back to you.

---

### Post by philcamlin on 2009-06-26
ok :D

---

### Post by Ayuthia on 2009-06-26
> **Nyhus said:**
> I've tryed this, works till i restart, then same problem. And yes, i guess its the beep i think.


Will try this and get back to you.

If the rmmod does stop it and you have pcspkr blacklisted, go ahead and remove the module again and update the initramfs:
```
sudo modprobe -r pcspkr
sudo update-initramfs -u
```That should fix when you reboot.

---

